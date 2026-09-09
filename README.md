
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ROAST & STEAM | Interactive 3D Cafe Experience</title>
    <!-- Tailwind CSS Engine for modern layout styling -->
    <script src="https://jsdelivr.net"></script>
    <!-- Three.js for high-performance 3D rendering -->
    <script src="https://cloudflare.com"></script>
    <!-- Premium Google Typography -->
    <link rel="preconnect" href="https://googleapis.com">
    <link rel="preconnect" href="https://gstatic.com" crossorigin>
    <link href="https://googleapis.com/css2?family=Playfair+Display:ital,wght@0,400..900;1,400..900&family=Plus+Jakarta+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Plus Jakarta Sans', sans-serif; background-color: #140d0a; }
        .font-serif { font-family: 'Playfair Display', serif; }
    </style>
</head>
<body class="text-[#f7f4f0] overflow-x-hidden relative h-screen w-full">

    <!-- 3D WebGL Canvas Layer Background -->
    <div id="canvas-container" class="absolute inset-0 z-0 w-full h-full pointer-events-auto"></div>

    <!-- UI/UX Front-End Overlay Menu -->
    <div class="absolute inset-0 z-10 flex flex-col justify-between p-6 md:p-12 pointer-events-none h-full w-full box-border">
        
        <!-- Navbar -->
        <header class="flex justify-between items-center w-full pointer-events-auto">
            <div class="text-xl font-bold tracking-widest text-[#d9b48f] hover:scale-105 transition-transform cursor-pointer">ROAST & STEAM.</div>
            <nav class="hidden md:flex gap-8 text-xs uppercase tracking-widest text-stone-400 font-semibold">
                <a href="#" class="hover:text-white transition-colors">Menu</a>
                <a href="#" class="hover:text-white transition-colors">Our Beans</a>
                <a href="#" class="hover:text-white transition-colors">Find Cafe</a>
            </nav>
            <button class="px-5 py-2.5 bg-[#4a2c11] hover:bg-[#5c3716] border border-[#d9b48f]/30 hover:border-[#d9b48f] text-xs uppercase tracking-wider rounded-full transition-all text-white font-medium shadow-lg shadow-black/40">
                Order Ahead
            </button>
        </header>

        <!-- Main Body Grid Content Layout -->
        <div class="grid grid-cols-1 md:grid-cols-2 w-full my-auto items-center pointer-events-none gap-8">
            
            <!-- Left Info Panel -->
            <main class="max-w-md flex flex-col gap-6 pointer-events-auto bg-black/10 backdrop-blur-sm p-6 rounded-2xl border border-white/5 md:bg-transparent md:backdrop-blur-none md:border-none">
                <span class="text-xs font-bold tracking-widest text-[#d9b48f] uppercase bg-[#4a2c11]/30 px-3 py-1 rounded-full w-fit">Brewed Fresh Everyday</span>
                <h1 class="text-4xl md:text-6xl font-serif tracking-tight text-white capitalize leading-tight font-bold">
                    Sip into <br />
                    Spatial Comfort.
                </h1>
                <p class="text-stone-400 text-sm leading-relaxed">
                    Experience our dynamic café menu interactively. Drag the screen to rotate the organic 3D bean, or click below to brew alternate drink profiles.
                </p>
                <div class="flex gap-4 mt-2">
                    <button class="px-6 py-3 bg-[#d9b48f] hover:bg-[#e4c4a7] text-[#140d0a] font-bold text-xs uppercase tracking-wider rounded-xl transition-all shadow-xl shadow-[#d9b48f]/10">
                        View Full Menu
                    </button>
                </div>
            </main>

            <!-- Right Interactive Dynamic Control Panel -->
            <div class="flex flex-col gap-3 max-w-sm md:ml-auto w-full pointer-events-auto bg-black/40 backdrop-blur-md p-6 rounded-2xl border border-white/10 shadow-2xl">
                <h3 class="text-xs uppercase tracking-widest text-[#d9b48f] font-bold mb-2">Select Your Blend</h3>
                
                <!-- Drink Option 1 -->
                <button onclick="changeDrink('espresso', '#4a2c11')" id="btn-espresso" class="drink-btn w-full text-left p-4 rounded-xl border transition-all flex justify-between items-center bg-[#4a2c11]/30 border-[#d9b48f] text-white shadow-lg">
                    <div>
                        <div class="font-bold text-sm text-white">Nitro Espresso</div>
                        <div class="text-xs text-stone-300 mt-1" id="desc-espresso">Single-origin Ethiopian beans cold-pressed over 18 hours.</div>
                    </div>
                    <div class="w-4 h-4 rounded-full shrink-0 ml-2 bg-[#4a2c11] border border-white/20"></div>
                </button>

                <!-- Drink Option 2 -->
                <button onclick="changeDrink('matcha', '#607c3c')" id="btn-matcha" class="drink-btn w-full text-left p-4 rounded-xl border transition-all flex justify-between items-center bg-transparent border-stone-800 text-stone-400 hover:border-stone-700">
                    <div>
                        <div class="font-bold text-sm text-white">Ceremonial Matcha</div>
                        <div class="text-xs text-stone-300 mt-1 hidden" id="desc-matcha">Stone-ground Uji matcha whisked gently with organic oatmilk.</div>
                    </div>
                    <div class="w-4 h-4 rounded-full shrink-0 ml-2 bg-[#607c3c] border border-white/20"></div>
                </button>

                <!-- Drink Option 3 -->
                <button onclick="changeDrink('vanilla', '#d9b48f')" id="btn-vanilla" class="drink-btn w-full text-left p-4 rounded-xl border transition-all flex justify-between items-center bg-transparent border-stone-800 text-stone-400 hover:border-stone-700">
                    <div>
                        <div class="font-bold text-sm text-white">Vanilla Cream Cold Brew</div>
                        <div class="text-xs text-stone-300 mt-1 hidden" id="desc-vanilla">Slow-steeped signature blend topped with sweet vanilla cream sweet foam.</div>
                    </div>
                    <div class="w-4 h-4 rounded-full shrink-0 ml-2 bg-[#d9b48f] border border-white/20"></div>
                </button>
            </div>

        </div>

        <!-- Footer Section -->
        <footer class="flex justify-between items-center text-[10px] uppercase tracking-wider text-stone-500 pointer-events-auto">
            <div>© 2026 ROAST & STEAM Co.</div>
            <div class="animate-pulse">Drag 3D space to rotate object</div>
        </footer>

    </div>

    <!-- Three.js Engine Logic Controller -->
    <script>
        let scene, camera, renderer, coffeeMesh;
        const container = document.getElementById('canvas-container');

        function init3D() {
            scene = new THREE.Scene();
            camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 0.1, 1000);
            camera.position.z = 4.5;

            renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            renderer.setSize(window.innerWidth, window.innerHeight);
            renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
            container.appendChild(renderer.domElement);

            // Studio Lights setup
            scene.add(new THREE.AmbientLight(0xffffff, 0.8));
            const dirLight1 = new THREE.DirectionalLight(0xfffcf7, 1.5);
            dirLight1.position.set(5, 5, 5);
            scene.add(dirLight1);

            // Floating Central Model Mesh Shape
            const geometry = new THREE.IcosahedronGeometry(1.2, 3);
            const material = new THREE.MeshStandardMaterial({
                color: new THREE.Color('#4a2c11'), // Starting Espresso theme
                roughness: 0.15,
                metalness: 0.1
            });

            coffeeMesh = new THREE.Mesh(geometry, material);
            scene.add(coffeeMesh);
            animate();
        }

        let clock = new THREE.Clock();
        function animate() {
            requestAnimationFrame(animate);
            const elapsedTime = clock.getElapsedTime();

            if (coffeeMesh) {
                coffeeMesh.rotation.y = elapsedTime * 0.35;
                coffeeMesh.rotation.x = Math.sin(elapsedTime * 0.2) * 0.15;
                const pulse = 1.0 + Math.sin(elapsedTime * 1.5) * 0.04;
                coffeeMesh.scale.set(pulse, pulse, pulse);
            }
            renderer.render(scene, camera);
        }

        // Live Dynamic State Change (Connects UI clicks seamlessly to 3D color shifts)
        function changeDrink(drinkKey, hexColor) {
            if (coffeeMesh) {
                coffeeMesh.material.color.set(hexColor);
            }

            document.querySelectorAll('.drink-btn').forEach(btn => {
                btn.classList.remove('bg-[#4a2c11]/30', 'border-[#d9b48f]', 'text-white', 'shadow-lg');
                btn.classList.add('bg-transparent', 'border-stone-800', 'text-stone-400');
            });

            const activeBtn = document.getElementById(`btn-${drinkKey}`);
            activeBtn.classList.remove('bg-transparent', 'border-stone-800', 'text-stone-400');
            activeBtn.classList.add('bg-[#4a2c11]/30', 'border-[#d9b48f]', 'text-white', 'shadow-lg');

            document.getElementById('desc-espresso').classList.add('hidden');
            document.getElementById('desc-matcha').classList.add('hidden');
            document.getElementById('desc-vanilla').classList.add('hidden');
            document.getElementById(`desc-${drinkKey}`).classList.remove('hidden');
        }

        // Window scaling and drag controls tracking
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
