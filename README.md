<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>India GlobalCine - Perfect Advanced Post & Video Editor</title>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Anton&family=Montserrat:wght@800;900&family=Oswald:wght@700&display=swap" rel="stylesheet">
    
    <style>
        /* ==========================================================================
           INDIA GLOBALCINE - ADVANCED PREMIUM CSS
           ========================================================================== */
        
        :root {
            --bg-dark: #121212;
            --panel-bg: #1e1e1e;
            --primary-accent: #ff2a2a;
            --primary-hover: #cc0000;
            --text-light: #ffffff;
            --text-muted: #aaaaaa;
            --border-color: #333333;
            
            /* Perfect Instagram Portrait Feed Size (4:5 Aspect Ratio) */
            --post-width: 1080px;
            --post-height: 1350px; 
            
            --news-red: #e61919;
            --news-black: #000000;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-light);
            display: flex;
            height: 100vh;
            overflow: hidden;
        }

        /* --- ADVANCED CONTROL PANEL --- */
        .editor-sidebar {
            width: 420px;
            background-color: var(--panel-bg);
            border-right: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            box-shadow: 10px 0 30px rgba(0,0,0,0.8);
            z-index: 10;
        }

        .sidebar-header {
            padding: 25px;
            background: #111;
            border-bottom: 2px solid var(--primary-accent);
            text-align: center;
        }

        .sidebar-header h1 {
            font-family: 'Oswald', sans-serif;
            font-size: 28px;
            color: #ffffff;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        .sidebar-header h1 span { color: var(--primary-accent); }

        .control-group-container {
            padding: 20px;
            overflow-y: auto;
            flex-grow: 1;
        }

        .control-group {
            margin-bottom: 25px;
            background: #252525;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid var(--primary-accent);
        }

        .control-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 800;
            font-size: 13px;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .form-control {
            width: 100%;
            padding: 14px;
            background-color: #111;
            border: 1px solid var(--border-color);
            color: #fff;
            border-radius: 4px;
            font-size: 15px;
            font-family: 'Montserrat', sans-serif;
            font-weight: bold;
        }
        .form-control:focus {
            outline: none;
            border-color: var(--primary-accent);
        }
        textarea.form-control { resize: vertical; min-height: 100px; }

        .file-upload-wrapper {
            position: relative;
            width: 100%;
            height: 70px;
            border: 2px dashed #555;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            background: #1a1a1a;
            transition: all 0.3s ease;
        }
        .file-upload-wrapper:hover { border-color: var(--primary-accent); }
        .file-upload-wrapper input[type="file"] {
            position: absolute; width: 100%; height: 100%; opacity: 0; cursor: pointer;
        }

        .action-buttons {
            padding: 20px;
            background-color: #111;
            border-top: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .btn {
            width: 100%;
            padding: 18px;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            font-weight: 900;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .btn:disabled { opacity: 0.7; cursor: not-allowed; }
        
        .btn-primary { background-color: var(--primary-accent); color: white; }
        .btn-primary:hover:not(:disabled) { background-color: var(--primary-hover); }
        
        .btn-secondary { background-color: #2c3e50; color: white; border: 1px solid #34495e; }
        .btn-secondary:hover:not(:disabled) { background-color: #34495e; }
        
        .btn-success { background-color: #00cc44; color: white; box-shadow: 0 4px 15px rgba(0,204,68,0.3); }
        .btn-success:hover:not(:disabled) { background-color: #00b33c; }

        /* --- PREVIEW CANVAS (INSTAGRAM FEED SIZE) --- */
        .preview-area {
            flex-grow: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            background: radial-gradient(circle at center, #333 0%, #000 100%);
            overflow: hidden;
            padding: 20px;
        }

        .canvas-scaler {
            position: relative;
            width: calc(100vh * (1080/1350) * 0.95); 
            height: calc(100vh * 0.95);
            box-shadow: 0 0 50px rgba(0, 0, 0, 1);
        }

        /* EXACT 1080x1350 DIMENSIONS FOR INSTAGRAM FEED/CAROUSEL */
        .instagram-post {
            position: absolute;
            top: 0; left: 0;
            width: var(--post-width);
            height: var(--post-height);
            background-color: #ffffff;
            transform-origin: top left;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        /* --- TOP HEADER (WHITE TEXT AREA) --- */
        .post-header-area {
            background-color: #ffffff;
            padding: 45px 30px 20px 30px; 
            z-index: 5;
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
            overflow: hidden; 
        }

        .main-breaking {
            font-family: 'Impact', 'Anton', sans-serif;
            font-size: 215px; 
            line-height: 0.8;
            color: var(--news-black);
            text-transform: uppercase;
            text-align: center;
            margin-bottom: 35px;
            letter-spacing: -1px;
            white-space: nowrap; 
            transform: scale(1.25, 1.3); 
        }

        .sub-headline {
            font-family: 'Montserrat', sans-serif;
            font-weight: 900;
            font-size: 50px;
            line-height: 1.25;
            color: var(--news-black);
            text-transform: uppercase;
            text-align: center;
            width: 95%;
        }

        .highlight-red {
            background-color: var(--news-red);
            color: white;
            padding: 2px 15px;
            display: inline-block;
            margin: 0 8px;
        }

        /* --- MEDIA AREA WITH SMOOTH FADE TRANSITION --- */
        .post-media-area {
            flex-grow: 1;
            position: relative;
            background-color: #000000; /* Darker base for better HD contrast */
            width: 100%;
            overflow: hidden;
        }

        /* FIXED PERFECT FADE - No Straight Lines, Less Blur, Clean Transition */
        .post-media-area::before {
            content: '';
            position: absolute;
            top: 0; 
            left: 0;
            width: 100%;
            height: 90px; /* Shorter fade for maximum image/video visibility */
            background: linear-gradient(to bottom, rgba(255,255,255,1) 0%, rgba(255,255,255,0) 100%);
            z-index: 2;
            pointer-events: none;
        }

        .media-content {
            width: 100%;
            height: 100%;
            object-fit: cover;
            position: absolute;
            top: 0; left: 0;
            z-index: 1;
        }

        /* --- OVERLAYS (DATE & LOGO) --- */
        .overlay-layer {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            pointer-events: none;
            z-index: 10;
        }

        .date-box {
            position: absolute;
            bottom: 30px;
            left: 30px;
            background-color: var(--news-red);
            color: white;
            padding: 10px 25px;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        .date-number {
            font-family: 'Impact', 'Anton', sans-serif;
            font-size: 90px;
            line-height: 0.9;
            letter-spacing: -2px;
        }
        .date-month {
            font-family: 'Montserrat', sans-serif;
            font-weight: 900;
            font-size: 32px;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: -5px;
        }

        .branding-corner {
            position: absolute;
            bottom: 30px;
            right: 30px;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.8);
        }

        .custom-logo {
            width: 180px;
            height: auto;
            margin-bottom: 10px;
            border-radius: 50%;
            box-shadow: 0 5px 15px rgba(0,0,0,0.5);
            display: none; 
        }

        .brand-text {
            font-family: 'Montserrat', sans-serif;
            color: white;
            font-size: 28px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        .brand-text span {
            color: var(--news-red);
        }

        /* --- PREMIUM NOTIFICATION & MOBILE FIXES --- */
        #advanced-toast {
            position: fixed; top: -100px; left: 50%; transform: translateX(-50%);
            background: #00cc44; color: white; padding: 15px 30px; border-radius: 50px;
            font-family: 'Montserrat', sans-serif; font-weight: 800; font-size: 16px;
            box-shadow: 0 10px 30px rgba(0, 204, 68, 0.4); z-index: 100000;
            transition: top 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            display: flex; align-items: center; gap: 10px; white-space: nowrap;
        }
        #advanced-toast.show { top: 30px; }

        #recording-overlay {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
            background: rgba(0,0,0,0.9); z-index: 9999;
            display: none; flex-direction: column; align-items: center; justify-content: center;
            color: white; font-family: 'Montserrat', sans-serif; text-align: center;
        }
        #recording-overlay h2 { font-size: 24px; margin-bottom: 10px; color: #00cc44; }
        
        .mobile-modal {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.95); z-index: 10000;
            display: none; flex-direction: column; align-items: center; justify-content: center; padding: 20px;
        }
        .mobile-modal.active { display: flex; }
        .mobile-modal video { width: 100%; max-width: 400px; border: 2px solid #333; border-radius: 10px; margin-bottom: 20px; }
        
        .download-btn-massive {
            display: block; width: 100%; max-width: 350px; padding: 25px; background: #00cc44; color: white;
            text-decoration: none; text-align: center; font-size: 20px; font-weight: 900; border-radius: 10px;
            margin-bottom: 15px; text-transform: uppercase; font-family: 'Montserrat', sans-serif;
            box-shadow: 0 10px 20px rgba(0, 204, 68, 0.3);
        }
        .close-btn { background: #333; color: white; padding: 15px 40px; border: none; border-radius: 8px; font-weight: bold; font-size: 16px; cursor: pointer; }

        @media (max-width: 900px) {
            body { flex-direction: column; overflow-y: auto; }
            .editor-sidebar { width: 100%; border-right: none; }
            .preview-area { min-height: 80vh; padding: 10px; }
            .canvas-scaler { width: calc(100vw * 0.95); height: calc((100vw * 0.95) * (1350/1080)); }
        }
    </style>
</head>
<body>

    <div id="advanced-toast">✅ Download Started! Check your notifications.</div>

    <aside class="editor-sidebar">
        <div class="sidebar-header">
            <h1>India <span>GlobalCine</span></h1>
        </div>

        <div class="control-group-container">
            
            <div class="control-group">
                <label>Main Heading (Giant Text)</label>
                <input type="text" id="input-breaking" class="form-control" value="BREAKING">
            </div>

            <div class="control-group">
                <label>Full Headline</label>
                <textarea id="input-headline" class="form-control">MP RAGHAV CHADHA REPLIED AFTER {AAP STOPPED HIM} FROM SPEAKING IN PARLIAMENT</textarea>
                <small style="color:#777; font-size: 11px; display:block; margin-top:5px; font-weight:normal;">* Use {brackets} to highlight words in RED box.</small>
            </div>

            <div style="display:flex; gap:10px;">
                <div class="control-group" style="flex:1;">
                    <label>Date (Num)</label>
                    <input type="text" id="input-date-num" class="form-control" value="03">
                </div>
                <div class="control-group" style="flex:1;">
                    <label>Month</label>
                    <input type="text" id="input-date-month" class="form-control" value="APRIL">
                </div>
            </div>

            <div class="control-group">
                <label>Upload Background Photo/Video</label>
                <div class="file-upload-wrapper">
                    <span style="color: #888; font-weight: bold; pointer-events: none;">📸 Choose Media</span>
                    <input type="file" id="media-upload" accept="image/*,video/*">
                </div>
            </div>
            
            <div class="control-group">
                <label>Upload Logo (Bottom Right)</label>
                <div class="file-upload-wrapper">
                    <span style="color: #888; font-weight: bold; pointer-events: none;">🛡️ Choose Logo Image</span>
                    <input type="file" id="logo-upload" accept="image/*">
                </div>
            </div>

        </div>

        <div class="action-buttons">
            <button id="btn-download-vid" class="btn btn-success" style="display: none;">
                📥 DOWNLOAD COMPLETE MP4 VIDEO
            </button>
            
            <button id="btn-download-img" class="btn btn-primary">
                Download Post as Image
            </button>
        </div>
    </aside>

    <main class="preview-area">
        
        <div id="recording-overlay">
            <h2 id="rec-status">STITCHING HD VIDEO & TEXT...</h2>
            <p>Please wait and do not close the browser.</p>
        </div>

        <div class="canvas-scaler" id="scaler">
            
            <div id="post-canvas" class="instagram-post">
                
                <div class="post-header-area">
                    <div class="main-breaking" id="render-breaking">BREAKING</div>
                    <div class="sub-headline" id="render-headline">
                        MP RAGHAV CHADHA REPLIED AFTER <span class="highlight-red">AAP STOPPED HIM</span> FROM SPEAKING IN PARLIAMENT
                    </div>
                </div>

                <div class="post-media-area">
                    <img id="render-media-img" class="media-content" src="" style="display:none;" alt="">
                    <video id="render-media-vid" class="media-content" style="display:none;" loop playsinline webkit-playsinline muted crossorigin="anonymous"></video>
                    
                    <div class="overlay-layer">
                        <div class="date-box">
                            <div class="date-number" id="render-date-num">03</div>
                            <div class="date-month" id="render-date-month">APRIL</div>
                        </div>

                        <div class="branding-corner">
                            <img id="render-logo" class="custom-logo" src="" alt="Logo">
                            <div class="brand-text">
                                INDIA <span>GLOBALCINE</span>
                            </div>
                        </div>
                    </div>
                </div>
                
            </div>

        </div>
    </main>

    <div class="mobile-modal" id="download-modal">
        <h2 style="color:white; margin-bottom: 20px; text-align:center;">✅ HD MP4 Video Ready!</h2>
        <video id="final-video-preview" controls playsinline webkit-playsinline loop></video>
        
        <a id="force-download-link" class="download-btn-massive" href="#" download="IndiaGlobalCine_HD_Video.mp4">
            📥 CLICK HERE IF DOWNLOAD DIDN'T START
        </a>
        <button class="close-btn" onclick="document.getElementById('download-modal').classList.remove('active')">Close</button>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            function showNotification(message) {
                const toast = document.getElementById('advanced-toast');
                toast.innerHTML = message;
                toast.classList.add('show');
                setTimeout(() => {
                    toast.classList.remove('show');
                }, 4000);
            }

            function scaleCanvas() {
                const scaler = document.getElementById('scaler');
                const post = document.getElementById('post-canvas');
                const parentW = scaler.parentElement.offsetWidth;
                const parentH = scaler.parentElement.offsetHeight;
                const scale = Math.min(parentW / 1080, parentH / 1350) * 0.95;
                post.style.transform = `scale(${scale})`;
                scaler.style.width = `${1080 * scale}px`;
                scaler.style.height = `${1350 * scale}px`;
            }
            window.addEventListener('resize', scaleCanvas);
            scaleCanvas();

            document.getElementById('input-breaking').addEventListener('input', e => {
                document.getElementById('render-breaking').textContent = e.target.value.toUpperCase();
            });
            document.getElementById('input-headline').addEventListener('input', e => {
                document.getElementById('render-headline').innerHTML = e.target.value.toUpperCase().replace(/\{(.*?)\}/g, '<span class="highlight-red">$1</span>');
            });
            document.getElementById('input-date-num').addEventListener('input', e => {
                document.getElementById('render-date-num').textContent = e.target.value;
            });
            document.getElementById('input-date-month').addEventListener('input', e => {
                document.getElementById('render-date-month').textContent = e.target.value.toUpperCase();
            });

            document.getElementById('media-upload').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (!file) return;

                const fileURL = URL.createObjectURL(file);
                const isVideo = file.type.startsWith('video/');
                
                const imgElement = document.getElementById('render-media-img');
                const vidElement = document.getElementById('render-media-vid');
                const vidDownloadBtn = document.getElementById('btn-download-vid');

                if (isVideo) {
                    imgElement.style.display = 'none';
                    vidElement.style.display = 'block';
                    vidElement.src = fileURL;
                    vidElement.muted = true; 
                    vidElement.play();
                    
                    vidDownloadBtn.style.display = 'block';
                } else {
                    vidElement.style.display = 'none';
                    vidElement.pause();
                    imgElement.style.display = 'block';
                    imgElement.src = fileURL;
                    
                    vidDownloadBtn.style.display = 'none';
                }
            });

            document.getElementById('logo-upload').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (!file) return;
                const imgElement = document.getElementById('render-logo');
                imgElement.src = URL.createObjectURL(file);
                imgElement.style.display = 'block'; 
            });

            // HD IMAGE DOWNLOADER (Scale bumped to 2 for High Definition)
            document.getElementById('btn-download-img').addEventListener('click', function() {
                const postCanvas = document.getElementById('post-canvas');
                const originalTransform = postCanvas.style.transform;
                postCanvas.style.transform = 'none';
                
                const btn = this;
                const originalText = btn.innerHTML;
                btn.innerHTML = 'GENERATING HD IMAGE...';
                btn.disabled = true;

                html2canvas(postCanvas, { 
                    scale: 2, /* Increased scale for HD output */
                    useCORS: true, 
                    backgroundColor: '#ffffff' 
                }).then(canvas => {
                    const link = document.createElement('a');
                    link.download = `IndiaGlobalCine_HD_${new Date().getTime()}.jpg`;
                    link.href = canvas.toDataURL('image/jpeg', 1.0); 
                    link.click();
                    
                    postCanvas.style.transform = originalTransform;
                    btn.innerHTML = originalText;
                    btn.disabled = false;
                    showNotification("📸 HD Image Downloaded Successfully!");
                });
            });

            // HD MP4 VIDEO DOWNLOADER
            document.getElementById('btn-download-vid').addEventListener('click', async function() {
                const vidElement = document.getElementById('render-media-vid');
                const imgElement = document.getElementById('render-media-img');
                const postCanvas = document.getElementById('post-canvas');
                const mediaArea = document.querySelector('.post-media-area');
                const overlay = document.getElementById('recording-overlay');
                const statusTxt = document.getElementById('rec-status');

                const originalTransform = postCanvas.style.transform;
                postCanvas.style.transform = 'none'; 
                overlay.style.display = 'flex';
                statusTxt.innerText = 'READING YOUR TEXT & DESIGN...';

                try {
                    const originalPostBg = postCanvas.style.backgroundColor;
                    const originalMediaBg = mediaArea.style.backgroundColor;
                    const originalVidDisplay = vidElement.style.display;
                    const originalImgDisplay = imgElement.style.display;

                    postCanvas.style.backgroundColor = 'transparent';
                    mediaArea.style.backgroundColor = 'transparent';
                    vidElement.style.display = 'none'; 
                    imgElement.style.display = 'none'; 
                    
                    const uiCanvas = await html2canvas(postCanvas, { scale: 1, backgroundColor: null, useCORS: true });
                    
                    postCanvas.style.backgroundColor = originalPostBg;
                    mediaArea.style.backgroundColor = originalMediaBg;
                    vidElement.style.display = originalVidDisplay;
                    imgElement.style.display = originalImgDisplay;
                    postCanvas.style.transform = originalTransform;

                    const recCanvas = document.createElement('canvas');
                    recCanvas.width = 1080;
                    recCanvas.height = 1350;
                    const ctx = recCanvas.getContext('2d');
                    
                    const mY = (mediaArea.getBoundingClientRect().top - postCanvas.getBoundingClientRect().top) * (1350/postCanvas.getBoundingClientRect().height);
                    const mH = mediaArea.getBoundingClientRect().height * (1350/postCanvas.getBoundingClientRect().height);

                    const canvasStream = recCanvas.captureStream(30);
                    let audioTracks = [];
                    if (vidElement.captureStream) audioTracks = vidElement.captureStream().getAudioTracks();
                    else if (vidElement.mozCaptureStream) audioTracks = vidElement.mozCaptureStream().getAudioTracks();
                    
                    let finalStream = canvasStream;
                    if (audioTracks.length > 0) {
                        finalStream = new MediaStream([...canvasStream.getVideoTracks(), ...audioTracks]);
                    }

                    let mimeType = 'video/mp4'; 
                    if (!MediaRecorder.isTypeSupported('video/mp4')) {
                        mimeType = 'video/webm'; 
                    }

                    // Boosted Bitrate to 10Mbps for HD Quality
                    const recorder = new MediaRecorder(finalStream, { 
                        mimeType: mimeType,
                        videoBitsPerSecond: 10000000 
                    });
                    
                    const chunks = [];
                    recorder.ondataavailable = e => { if (e.data.size > 0) chunks.push(e.data); };

                    vidElement.loop = false;
                    vidElement.muted = false; 
                    vidElement.currentTime = 0;
                    await vidElement.play();
                    await new Promise(r => setTimeout(r, 200)); 

                    statusTxt.innerText = 'RECORDING HD MP4 VIDEO... DO NOT CLOSE';

                    let isRecording = true;
                    function drawVideoFrame() {
                        if (!isRecording) return;
                        
                        ctx.fillStyle = '#ffffff';
                        ctx.fillRect(0, 0, 1080, 1350);
                        
                        ctx.fillStyle = '#000000'; // Dark background under video
                        ctx.fillRect(0, mY, 1080, mH);

                        if (vidElement.readyState >= 2) {
                            const ratio = vidElement.videoWidth / vidElement.videoHeight;
                            const targetRatio = 1080 / mH;
                            let sw, sh, sx, sy;

                            if (ratio > targetRatio) {
                                sh = vidElement.videoHeight;
                                sw = sh * targetRatio;
                                sx = (vidElement.videoWidth - sw) / 2;
                                sy = 0;
                            } else {
                                sw = vidElement.videoWidth;
                                sh = sw / targetRatio;
                                sx = 0;
                                sy = (vidElement.videoHeight - sh) / 2;
                            }
                            ctx.drawImage(vidElement, sx, sy, sw, sh, 0, mY, 1080, mH);
                        }

                        ctx.drawImage(uiCanvas, 0, 0, 1080, 1350);

                        requestAnimationFrame(drawVideoFrame);
                    }

                    recorder.start();
                    drawVideoFrame();

                    vidElement.onended = () => {
                        isRecording = false;
                        recorder.stop();
                    };

                    recorder.onstop = () => {
                        const blob = new Blob(chunks, { type: mimeType });
                        const url = URL.createObjectURL(blob);
                        const ext = mimeType.includes('mp4') ? 'mp4' : 'webm';
                        const filename = `IndiaGlobalCine_HD_Video_${Date.now()}.${ext}`;

                        overlay.style.display = 'none';
                        vidElement.loop = true;
                        vidElement.muted = true;
                        vidElement.play();

                        const downloadLink = document.createElement('a');
                        downloadLink.style.display = 'none';
                        downloadLink.href = url;
                        downloadLink.download = filename;
                        document.body.appendChild(downloadLink);
                        
                        downloadLink.click();
                        showNotification("✅ HD Video Download Started! Check your browser downloads.");
                        
                        setTimeout(() => {
                            document.body.removeChild(downloadLink);
                            const modal = document.getElementById('download-modal');
                            const finalVideoPreview = document.getElementById('final-video-preview');
                            const forceDownloadBtn = document.getElementById('force-download-link');

                            finalVideoPreview.src = url;
                            forceDownloadBtn.href = url;
                            forceDownloadBtn.download = filename;
                            modal.classList.add('active');
                        }, 500);
                    };

                    setTimeout(() => {
                        if (isRecording) {
                            isRecording = false;
                            recorder.stop();
                        }
                    }, (vidElement.duration * 1000) + 2000 || 15000);

                } catch(error) {
                    console.error(error);
                    alert("Error processing HD video. Make sure your browser allows Canvas recording.");
                    overlay.style.display = 'none';
                    postCanvas.style.transform = originalTransform;
                }
            });

        });
    </script>
</body>
</html>
