<template>
  <div ref="modelContainer" style="width: 100vw; height: 100vh;"></div>
</template>

<script>
import * as THREE from 'three';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader';

export default {
  name: "ThreeModelViewer",
  mounted() {
    this.initThreeJS();
  },
  methods: {
    initThreeJS() {
      const width = this.$refs.modelContainer.offsetWidth;
      const height = this.$refs.modelContainer.offsetHeight;

      // 创建场景
      const scene = new THREE.Scene();

      // 添加相机
      const camera = new THREE.PerspectiveCamera(75, width / height, 0.1, 1000);
      camera.position.z = 6;
      camera.position.y = 0;

      // 创建渲染器并将其绑定到DOM元素上
      const renderer = new THREE.WebGLRenderer({ antialias: true });
      renderer.setSize(width, height);
      this.$refs.modelContainer.appendChild(renderer.domElement);

      // 添加光源
      const ambientLight = new THREE.AmbientLight(0xffffff, 3);
      scene.add(ambientLight);

      const directionalLight = new THREE.DirectionalLight(0xffffff, 1);
      directionalLight.position.set(0, 20, 0); // 调整为合适的位置
      scene.add(directionalLight);
      
      // 加载模型
      const loader = new GLTFLoader();
      loader.load(
        '/ash_baby.glb',  // 这里替换为你的模型路径
        (gltf) => {
          scene.add(gltf.scene);
          renderer.render(scene, camera); // 初始渲染一次
        },
        undefined,
        function (error) {
          console.error('An error happened', error);
        }
      );

      // 设置模型初始位置
      scene.position.set(0, -2.5, 0);


      // 添加控制器
      const controls = new OrbitControls(camera, renderer.domElement);
      // 增加控制范围
      controls.minDistance = 1;
      controls.maxDistance = 20;
      controls.addEventListener('change', () => renderer.render(scene, camera)); // 监听鼠标、触控控制
      
      // 设置拖拽阻尼
      controls.enableDamping = true;
      controls.dampingFactor = 0.1;

      // 设置初始化相机从远处拉到近处
      controls.maxPolarAngle = Math.PI / 2;

      // 渲染循环
      function animate() {
        requestAnimationFrame(animate);
        // Y轴缓慢旋转
        scene.rotation.y -= 0.01;
        renderer.render(scene, camera);
      }

      animate();
    }
  }
}
</script>
