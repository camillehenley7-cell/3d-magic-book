<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <!-- 核心补充：限制默认的缩放行为，防止双指操作时触发系统级网页放大 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>3D 跨页魔法绘本 - 4K 移动端旗舰版</title>
    <style>
        :root {
            /* 原生 4000px 视网膜级分辨率底板 */
            --book-width: 4000px; 
            --book-height: 1452px; 
            --btn-bg: rgba(26, 26, 26, 0.98);
            --btn-hover: rgba(0, 0, 0, 1);
            --z-gap: 50px; /* 超大物理间距，防止任何微小的 Z-fighting 闪动 */
        }

        html, body {
            background-color: #000; 
            margin: 0; padding: 0;
            overflow: hidden; 
            width: 100%; height: 100%;
            touch-action: none; 
            -webkit-user-select: none;
            user-select: none;
        }

        body {
            background-image: url('7af60992522253a99c4fdb994dca1423.png');
            background-size: cover; background-position: center; background-attachment: fixed;
        }

        /* 顶级透视舞台：45000px 消除边缘畸变 */
        .app-wrapper {
            display: flex; justify-content: center; align-items: center;
            height: 100vh; width: 100vw; position: relative;
            cursor: grab;
            perspective: 45000px; 
            perspective-origin: center;
        }
        .app-wrapper:active { cursor: grabbing; }

        /* 2D 缩放平移层 */
        #viewManipulator {
            display: flex; justify-content: center; align-items: center;
            transform-origin: center center;
            transform-style: preserve-3d;
        }

        .book {
            width: var(--book-width); 
            height: var(--book-height);
            position: relative;
            transform-style: preserve-3d;
            pointer-events: none;
        }

        /* 物理装订层 */
        .book::after {
            content: "";
            position: absolute; left: 50%; top: 0;
            width: 16px; height: 100%;
            background: #000;
            transform: translateX(-50%) translateZ(1200px); 
            z-index: 100000;
            box-shadow: 0 0 80px rgba(0,0,0,1);
            pointer-events: none;
        }

        /* 页面主体 */
        .page {
            width: 50%; height: 100%;
            position: absolute; right: 0; top: 0;
            transform-origin: left center;
            transform-style: preserve-3d; 
            margin-left: -2px;
            background-color: #000; 
            transform: translate3d(0, 0, calc(var(--z) * var(--z-gap) + var(--lift, 0px))) rotateY(0.01deg);
            transition: transform 1s cubic-bezier(0.25, 0, 0.1, 1);
            cursor: pointer;
            border-radius: 0 48px 48px 0;
            pointer-events: auto;
            visibility: hidden; 
        }

        .page.flipped {
            transform: translate3d(10px, 0, calc(var(--z) * var(--z-gap) + var(--lift, 0px))) rotateY(-179.99deg);
        }

        /* 原生高清纹理层：1:1 对齐原图 */
        .front, .back {
            position: absolute; width: 100%; height: 100%;
            -webkit-backface-visibility: hidden;
            backface-visibility: hidden;
            overflow: hidden; 
            background-color: #0a0a0a; 
            outline: 1px solid transparent; 
            background-size: 200.2% 100.2%; 
            background-repeat: no-repeat;
            
            image-rendering: -webkit-optimize-contrast;
            image-rendering: high-quality;
            -webkit-font-smoothing: antialiased;
        }

        .front {
            border-radius: 0 48px 48px 0;
            background-position: right;
            background-image: linear-gradient(to right, rgba(0,0,0,0.5) 0%, transparent 8%);
        }

        .back {
            border-radius: 48px 0 0 48px;
            transform: rotateY(180deg);
            background-position: left;
            background-image: linear-gradient(to left, rgba(0,0,0,0.5) 0%, transparent 8%);
        }

        .cover { background-image: url('封面.jpg') !important; background-size: 100% 100% !important; border-left: 8px solid #000; }
        .cover-back { background-image: url('封底.jpg') !important; background-size: 100% 100% !important; border-right: 8px solid #000; }

        .front::after, .back::after {
            content: ""; position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none; opacity: 0; transition: opacity 0.5s;
            background: linear-gradient(to right, rgba(0,0,0,0) 0%, rgba(0,0,0,0.3) 50%, rgba(0,0,0,0) 100%);
        }
        .page.flipping .front::after, .page.flipping .back::after { opacity: 0.5; }

        /* 胶囊按钮 */
        .expand-btn {
            position: absolute; right: 140px; top: 140px;
            background: var(--btn-bg); color: #fff; padding: 56px 180px; 
            border-radius: 400px; font-size: 60px; font-weight: 600; cursor: pointer; 
            border: 4px solid rgba(255,255,255,0.1); z-index: 600000; box-shadow: 0 60px 200px rgba(0,0,0,0.9);
            backdrop-filter: blur(140px); -webkit-backdrop-filter: blur(140px);
            transition: all 0.4s ease;
            display: flex; align-items: center; justify-content: center;
            pointer-events: auto;
        }
        .expand-btn:hover { background: var(--btn-hover); transform: scale(1.05) translateY(-8px); }
        .is-expanded .expand-btn { top: -250px; right: 0; background: #000; }

        /* 折页系统核心无缝平整修复 */
        .page-foldout { overflow: visible !important; }
        .page-foldout .front { 
            overflow: visible !important; 
            transform-style: preserve-3d !important; 
            border-radius: 0 !important; 
        }
        
        .foldout-container {
            position: absolute; width: 100%; height: 100%; right: 0; top: 0;
            transform-style: preserve-3d; visibility: hidden; opacity: 0;
            pointer-events: none; transition: opacity 0.5s;
            z-index: 500000;
        }
        .is-expanded .foldout-container { visibility: visible; opacity: 1; pointer-events: auto; }
        
        .flap {
            position: absolute; width: 100%; height: 100%; right: -100%; top: 0;
            transform-origin: left center; transform-style: preserve-3d;
            transition: transform 0.8s cubic-bezier(0.2, 0, 0, 1), box-shadow 0.8s;
            background-color: #0a0a0a; box-shadow: -100px 0 250px rgba(0,0,0,0.8);
            background-size: 400.2% 100.2% !important; background-repeat: no-repeat;
            image-rendering: high-quality;
            transform: translateZ(4px) rotateY(-180deg); 
        }
        .is-expanded .flap { 
            transform: translateZ(0px) rotateY(0deg); 
            box-shadow: none; 
        }

        .flap-1 { background-position: 66.6% !important; z-index: 10; }
        .flap-2 { background-position: 100% !important; z-index: 11; border-radius: 0 48px 48px 0; }
        .p14-left, .p15-left { background-size: 400.2% 100.2% !important; background-position: 0% !important; }
        .p14-right, .p15-right { background-size: 400.2% 100.2% !important; background-position: 33.3% !important; }

    </style>
</head>
<body>

    <div class="app-wrapper" id="appWrapper">
        <div id="viewManipulator">
            <div class="book" id="book">
                <!-- 0-12页 -->
                <div class="page"><div class="front cover"></div><div class="back" style="background-image: url('1.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('1.jpg')"></div><div class="back" style="background-image: url('2.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('2.jpg')"></div><div class="back" style="background-image: url('3.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('3.jpg')"></div><div class="back" style="background-image: url('4.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('4.jpg')"></div><div class="back" style="background-image: url('5.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('5.jpg')"></div><div class="back" style="background-image: url('6.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('6.jpg')"></div><div class="back" style="background-image: url('7.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('7.jpg')"></div><div class="back" style="background-image: url('8.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('8.jpg')"></div><div class="back" style="background-image: url('9.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('9.jpg')"></div><div class="back" style="background-image: url('10.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('10.jpg')"></div><div class="back" style="background-image: url('11.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('11.jpg')"></div><div class="back" style="background-image: url('12.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('12.jpg')"></div><div class="back" style="background-image: url('13.jpg')"></div></div>
                
                <div class="page"><div class="front" style="background-image: url('13.jpg')"></div><div class="back p14-left" style="background-image: url('14.jpg')"></div></div>
                
                <!-- 长图 14 -->
                <div class="page page-foldout" id="page14">
                    <div class="front p14-right" style="background-image: url('14.jpg')">
                        <div class="expand-btn" onclick="toggleFoldout(event, 'page14')">展开全图</div>
                        <div class="foldout-container">
                            <div class="flap flap-1" style="background-image: url('14.jpg')">
                                <div class="flap flap-2" style="background-image: url('14.jpg')"></div>
                            </div>
                        </div>
                    </div>
                    <div class="back p15-left" style="background-image: url('15.jpg')"></div>
                </div>

                <!-- 长图 15 -->
                <div class="page page-foldout" id="page15">
                    <div class="front p15-right" style="background-image: url('15.jpg')">
                        <div class="expand-btn" onclick="toggleFoldout(event, 'page15')">展开全图</div>
                        <div class="foldout-container">
                            <div class="flap flap-1" style="background-image: url('15.jpg')">
                                <div class="flap flap-2" style="background-image: url('15.jpg')"></div>
                            </div>
                        </div>
                    </div>
                    <div class="back" style="background-image: url('16.jpg')"></div>
                </div>

                <div class="page"><div class="front" style="background-image: url('16.jpg')"></div><div class="back" style="background-image: url('17.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('17.jpg')"></div><div class="back" style="background-image: url('18.jpg')"></div></div>
                <div class="page"><div class="front" style="background-image: url('18.jpg')"></div><div class="back cover-back"></div></div>
            </div>
        </div>
    </div>

    <script>
        const pages = document.querySelectorAll('.page');
        const book = document.getElementById('book');
        const manipulator = document.getElementById('viewManipulator');
        const appWrapper = document.getElementById('appWrapper');

        let currentPage = 0; 
        let curS = 1; 
        let tarS = 1;
        let isEngineRunning = false;

        // 交互参数
        let isDragging = false;
        let startPtrX = 0, startPtrY = 0;
        let panX = 0, panY = 0;
        let tarPanX = 0, tarPanY = 0;
        let ptrMoveDist = 0;

        // 多指缩放参数
        let pointerCache = [];
        let initialDistance = 0;
        let initialScale = 1;
        let isPinching = false;

        function updateAllPageZIndex() {
            pages.forEach((p, i) => {
                const flipped = p.classList.contains('flipped');
                const stackZ = flipped ? i : (pages.length - i);
                p.style.setProperty('--z', stackZ);
                
                if (!p.classList.contains('flipping') && !p.classList.contains('is-expanded')) {
                    p.style.zIndex = stackZ;
                }

                const isFlipping = p.classList.contains('flipping');
                const isExpanded = p.classList.contains('is-expanded');
                
                if (isFlipping || isExpanded || (i >= currentPage - 2 && i <= currentPage + 1)) {
                    p.style.visibility = 'visible';
                } else {
                    p.style.visibility = 'hidden';
                }
            });
        }

        function init() {
            updateAllPageZIndex();
            syncRenderLoop();
        }

        function getIsExp() { return !!document.querySelector('.page.is-expanded'); }

        function syncRenderLoop() {
            const isExp = getIsExp();
            const winW = window.innerWidth * 0.96;
            const viewW = isExp ? 8000 : 4000; 
            const baseS = Math.min(winW / viewW, 1.0);
            const scale = curS * baseS;
            
            manipulator.style.transform = `translate3d(${panX}px, ${panY}px, 0px) scale(${scale})`;
            
            let shift = 0;
            if (isExp) shift = -50; 
            else if (currentPage === 0) shift = -25;
            else if (currentPage === pages.length) shift = 25;
            book.style.transform = `translateX(${shift}%)`;
        }

        function startEngine() {
            if (isEngineRunning) return;
            isEngineRunning = true;

            function loop() {
                const sDiff = tarS - curS;
                const xDiff = tarPanX - panX;
                const yDiff = tarPanY - panY;

                if (Math.abs(sDiff) > 0.0001 || Math.abs(xDiff) > 0.5 || Math.abs(yDiff) > 0.5) {
                    curS += sDiff * 0.28;
                    panX += xDiff * 0.28;
                    panY += yDiff * 0.28;
                    syncRenderLoop();
                    requestAnimationFrame(loop);
                } else {
                    curS = tarS;
                    panX = tarPanX;
                    panY = tarPanY;
                    syncRenderLoop();
                    isEngineRunning = false;
                }
            }
            loop();
        }

        appWrapper.addEventListener('pointerdown', (e) => {
            if (e.pointerType === 'mouse' && e.button !== 0) return;
            if (e.target.closest('.expand-btn')) return; 

            pointerCache.push(e);
            
            if (pointerCache.length === 1) {
                isDragging = true;
                isPinching = false;
                startPtrX = e.clientX / curS - tarPanX;
                startPtrY = e.clientY / curS - tarPanY;
                ptrMoveDist = 0;
                appWrapper.setPointerCapture(e.pointerId);
            } else if (pointerCache.length === 2) {
                isDragging = false; 
                isPinching = true;
                initialDistance = Math.hypot(
                    pointerCache[0].clientX - pointerCache[1].clientX,
                    pointerCache[0].clientY - pointerCache[1].clientY
                );
                initialScale = tarS;
            }
            e.preventDefault();
        });

        appWrapper.addEventListener('pointermove', (e) => {
            const index = pointerCache.findIndex(p => p.pointerId === e.pointerId);
            if (index !== -1) pointerCache[index] = e;

            if (pointerCache.length === 2 && isPinching) {
                const currentDistance = Math.hypot(
                    pointerCache[0].clientX - pointerCache[1].clientX,
                    pointerCache[0].clientY - pointerCache[1].clientY
                );
                const scaleDiff = currentDistance / initialDistance;
                tarS = Math.min(Math.max(initialScale * scaleDiff, 0.4), 15.0);
                startEngine();
                return;
            }

            if (!isDragging) return;
            
            tarPanX = e.clientX / curS - startPtrX;
            tarPanY = e.clientY / curS - startPtrY;
            ptrMoveDist += Math.abs(e.movementX || 0) + Math.abs(e.movementY || 0);
            startEngine();
        });

        const handlePointerUp = (e) => {
            pointerCache = pointerCache.filter(p => p.pointerId !== e.pointerId);

            if (pointerCache.length < 2) {
                isPinching = false;
                initialDistance = 0;
            }

            if (pointerCache.length === 1) {
                isDragging = true;
                startPtrX = pointerCache[0].clientX / curS - tarPanX;
                startPtrY = pointerCache[0].clientY / curS - tarPanY;
            } else if (pointerCache.length === 0) {
                if (isDragging) {
                    isDragging = false;
                    appWrapper.releasePointerCapture(e.pointerId);

                    if (ptrMoveDist < 15 && !getIsExp()) {
                        const rect = book.getBoundingClientRect();
                        if (e.clientX < rect.left + rect.width / 2) goPrev(); else goNext();
                    }
                }
            }
        };

        appWrapper.addEventListener('pointerup', handlePointerUp);
        appWrapper.addEventListener('pointercancel', handlePointerUp);

        function goNext() {
            if (currentPage >= pages.length) return;
            const p = pages[currentPage];
            p.classList.add('flipping');
            p.style.setProperty('--lift', '800px'); 
            p.style.zIndex = "1000"; 
            p.classList.add('flipped');
            currentPage++;
            
            updateAllPageZIndex();
            
            setTimeout(() => {
                p.style.setProperty('--lift', '0px');
                p.classList.remove('flipping');
                updateAllPageZIndex(); 
            }, 1000);
            syncRenderLoop();
        }

        function goPrev() {
            if (currentPage <= 0) return;
            currentPage--;
            const p = pages[currentPage];
            p.classList.add('flipping');
            p.style.setProperty('--lift', '800px');
            p.style.zIndex = "1000";
            p.classList.remove('flipped');
            
            updateAllPageZIndex();
            
            setTimeout(() => {
                p.style.setProperty('--lift', '0px');
                p.classList.remove('flipping');
                updateAllPageZIndex();
            }, 1000);
            syncRenderLoop();
        }

        window.toggleFoldout = function(e, id) {
            e.preventDefault(); e.stopPropagation(); 
            const el = document.getElementById(id);
            const btn = e.currentTarget;
            if (!el.classList.contains('is-expanded')) {
                el.classList.add('is-expanded');
                btn.innerText = "收回全图";
                el.style.zIndex = "500000"; 
                el.style.setProperty('--lift', '2400px');
            } else {
                el.classList.remove('is-expanded');
                btn.innerText = "展开全图";
                el.style.setProperty('--lift', '0px');
            }
            updateAllPageZIndex();
            startEngine(); 
        };

        document.addEventListener('wheel', (e) => {
            e.preventDefault();
            tarS = Math.min(Math.max(tarS - e.deltaY * 0.003, 0.4), 15.0);
            startEngine();
        }, { passive: false }); 

        window.addEventListener('resize', syncRenderLoop);
        init();
    </script>
</body>
</html>
