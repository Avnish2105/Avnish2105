# Hi there! I'm Avnish Deshmukh 👋

Welcome to my GitHub profile! I'm a passionate robotics enthusiast and currently a tech team member at **MTT ROBOCON** (MIT Tech Team). To learn more about MTT, visit [MTT ROBOCON](https://robocon.mitwpu.edu.in/).

## 📫 How to reach me:
- **Email**: avnishd2105@gmail.com
- **LinkedIn**: [Avnish Deshmukh](https://www.linkedin.com/in/avnish-deshmukh-9a46b2234/?trk=people-guest_people_search-card&originalSubdomain=in)
- **Portfolio**: [Avnish2105.github.io](https://Avnish2105.github.io)

## ⚡ Technologies I work with:
- **Hardware**: ODrive S1, VESC smart BLDC motor drivers, STM32, TM4C microcontrollers
- **Tools**: Docker, Linux (Ubuntu), GitHub
- **Frameworks**: ROS2 (Robot Operating System), Embedded Systems

## 🌱 What I'm learning:
- Exploring whatever is required to **win ROBOCON**, with a focus on:
  - Computer Vision
  - Embedded MCU programming (mbed)
  - ROS2

## ⚡ Fun facts:
- Outside of coding, I enjoy tinkering with electronics and experimenting with new robotics hardware.
- My journey into robotics started with **electronics hardware**, and I always double-check the electronics if the code isn't working!

Let's connect and collaborate on innovative projects!
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crazy Cursor Animation</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background: black;
        }
        canvas {
            position: absolute;
            top: 0;
            left: 0;
        }
    </style>
</head>
<body>
    <canvas id="crazyCanvas"></canvas>
    <script>
        const canvas = document.getElementById("crazyCanvas");
        const ctx = canvas.getContext("2d");
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let particles = [];

        class Particle {
            constructor(x, y) {
                this.x = x;
                this.y = y;
                this.size = Math.random() * 8 + 2;
                this.speedX = (Math.random() - 0.5) * 6;
                this.speedY = (Math.random() - 0.5) * 6;
                this.color = `hsl(${Math.random() * 360}, 100%, 60%)`;
            }
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                this.size *= 0.95;
            }
            draw() {
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function handleParticles() {
            for (let i = 0; i < particles.length; i++) {
                particles[i].update();
                particles[i].draw();
                if (particles[i].size < 0.5) {
                    particles.splice(i, 1);
                    i--;
                }
            }
        }

        window.addEventListener("mousemove", (e) => {
            for (let i = 0; i < 5; i++) {
                particles.push(new Particle(e.x, e.y));
            }
        });

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            handleParticles();
            requestAnimationFrame(animate);
        }

        animate();

        window.addEventListener("resize", () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
