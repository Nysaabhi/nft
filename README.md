<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nysa NFT Feed</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #6c5ce7;
            --secondary-color: #00cec9;
            --text-color: #2d3436;
            --text-secondary: #636e72;
            --border-color: #dfe6e9;
            --background-color: #f9f9f9;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--background-color);
            color: var(--text-color);
            line-height: 1.6;
        }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 0 15px;
        }

        .post {
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .post:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        .post-header {
            display: flex;
            align-items: center;
            padding: 16px;
            border-bottom: 1px solid var(--border-color);
        }

        .post-avatar {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            object-fit: cover;
        }

        .post-info {
            margin-left: 16px;
            flex-grow: 1;
        }

        .post-author {
            font-weight: 600;
            font-size: 16px;
            color: var(--primary-color);
        }

        .post-date {
            font-size: 14px;
            color: var(--text-secondary);
        }

        .follow-btn {
            background-color: var(--secondary-color);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 500;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.1s ease;
        }

        .follow-btn:hover {
            background-color: #00b5b5;
            transform: scale(1.05);
        }

        .follow-btn.following {
            background-color: var(--primary-color);
        }

        .nft-image {
            width: 100%;
            height: 400px;
            object-fit: cover;
        }

        .post-content {
            padding: 20px;
        }

        .post-title {
            font-size: 30px;
            font-weight: 600;
            margin-bottom: 12px;
            color: var(--primary-color);
        }

        .post-text {
            font-size: 24px;
            color: var(--text-color);
            margin-bottom: 16px;
        }

        .nft-info {
            display: flex;
            justify-content: space-between;
            background-color: #f0f0f0;
            border-radius: 8px;
            padding: 12px;
            margin-bottom: 7px;
            flex-wrap: wrap;
        }

        .nft-info-item {
            font-size: 14px;
            white-space: nowrap;
            margin: 4px 4px;
        }

        .nft-info-item strong {
            color: var(--primary-color);
        }

        .post-actions {
            display: flex;
            justify-content: space-around;
            padding: 16px;
            border-top: 1px solid var(--border-color);
            background-color: #f8f9fa;
        }

        .action-btn {
            display: flex;
            align-items: center;
            background: none;
            border: none;
            color: var(--text-secondary);
            font-size: 14px;
            cursor: pointer;
            transition: color 0.3s ease, transform 0.1s ease;
        }

        .action-btn:hover {
            color: var(--primary-color);
            transform: scale(1.1);
        }

        .action-btn i {
            margin-right: 6px;
            font-size: 18px;
        }

        .bid-btn {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 500;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.1s ease;
        }

        .bid-btn:hover {
            background-color: #5b4cc7;
            transform: scale(1.05);
        }

        @media (max-width: 600px) {
            .container {
                padding: 0 10px;
            }

            .post-header {
                padding: 12px;
            }

            .post-avatar {
                width: 40px;
                height: 40px;
            }

            .post-author {
                font-size: 14px;
            }

            .post-date {
                font-size: 12px;
            }

            .follow-btn {
                padding: 6px 12px;
                font-size: 12px;
            }

            .nft-image {
                height: 700px;
            }

            .post-content {
                padding: 16px;
            }

            .post-title {
                font-size: 30px;
            }

            .post-text {
                font-size: 24px;
            }

            .nft-info {
                padding: 8px;
            }

            .nft-info-item {
                font-size: 12px;
                margin: 2px 4px;
            }

            .post-actions {
                padding: 12px;
            }

            .action-btn {
                font-size: 12px;
            }

            .action-btn i {
                font-size: 16px;
            }
        }
    </style>
</head>
<body>
    <div class="container" id="post-container"></div>

    <script>
        const posts = [
            {
                id: 1,
                author: "CryptoArtist",
                avatar: "https://i.pravatar.cc/150?img=1",
                date: "2h ago",
                image: "https://i.ibb.co/dkRj6z0/Whats-App-Image-2024-10-20-at-09-16-08-0798f91f.jpg",
                title: "Ethereal Dreams #42",
                content: "Explore the boundaries of reality with my latest NFT creation. This piece represents the fusion of technology and spirituality in our digital age.",
                likes: 1200,
                comments: 89,
                shares: 56,
                price: 2.5,
                currency: "ETH",
                collection: "Ethereal Dreams",
                blockchain: "Ethereum"
            },
            {
                id: 2,
                author: "PixelMaster",
                avatar: "https://i.pravatar.cc/150?img=2",
                date: "1d ago",
                image: "https://i.ibb.co/kMyZsYy/Whats-App-Image-2024-10-20-at-09-16-07-1901e522.jpg",
                title: "Crypto Punk Remix #007",
                content: "A fresh take on the iconic Crypto Punks. This NFT combines classic pixel art with modern crypto culture references.",
                likes: 3500,
                comments: 210,
                shares: 180,
                price: 1.8,
                currency: "ETH",
                collection: "Punk Remixed",
                blockchain: "Ethereum"
            },
            {
                id: 3,
                author: "FutureScape",
                avatar: "https://i.pravatar.cc/150?img=3",
                date: "3d ago",
                image: "https://i.ibb.co/Pxp031L/Whats-App-Image-2024-10-20-at-09-16-07-510389dd.jpg",
                title: "Neo Tokyo Skyline",
                content: "Immerse yourself in the vibrant future of Neo Tokyo with this animated NFT. Each frame tells a story of innovation and culture.",
                likes: 2800,
                comments: 156,
                shares: 95,
                price: 3.2,
                currency: "ETH",
                collection: "FutureScapes",
                blockchain: "Polygon"
            }
        ];

        function formatNumber(num) {
            if (num >= 1000000) return `${(num / 1000000).toFixed(1)}M`;
            if (num >= 1000) return `${(num / 1000).toFixed(1)}K`;
            return num.toString();
        }

        function createPostElement(post) {
            const postElement = document.createElement('div');
            postElement.className = 'post';
            postElement.innerHTML = `
                <div class="post-header">
                    <img src="${post.avatar}" alt="${post.author}" class="post-avatar">
                    <div class="post-info">
                        <div class="post-author">${post.author}</div>
                        <div class="post-date">${post.date}</div>
                    </div>
                    <button class="follow-btn">Follow</button>
                </div>
                <img src="${post.image}" alt="${post.title}" class="nft-image">
                <div class="post-content">
                    <h2 class="post-title">${post.title}</h2>
                    <p class="post-text">${post.content}</p>
                    <div class="nft-info">
                        <span class="nft-info-item"><strong>Price:</strong> ${post.price} ${post.currency}</span>
                        <span class="nft-info-item"><strong>Collection:</strong> ${post.collection}</span>
                        <span class="nft-info-item"><strong>Blockchain:</strong> ${post.blockchain}</span>
                    </div>
                    <button class="bid-btn">Place Bid</button>
                </div>
                <div class="post-actions">
                    <button class="action-btn like-btn" data-count="${post.likes}">
                        <i class="fas fa-heart"></i> <span>${formatNumber(post.likes)}</span>
                    </button>
                    <button class="action-btn">
                        <i class="fas fa-comment"></i> ${formatNumber(post.comments)}
                    </button>
                    <button class="action-btn">
                        <i class="fas fa-share"></i> ${formatNumber(post.shares)}
                    </button>
                    <button class="action-btn">
                        <i class="fas fa-bookmark"></i> Save
                    </button>
                </div>
            `;

            const followBtn = postElement.querySelector('.follow-btn');
            followBtn.addEventListener('click', () => {
                followBtn.classList.toggle('following');
                followBtn.textContent = followBtn.classList.contains('following') ? 'Following' : 'Follow';
            });

            const likeBtn = postElement.querySelector('.like-btn');
            likeBtn.addEventListener('click', () => {
                let count = parseInt(likeBtn.dataset.count);
                if (likeBtn.classList.contains('liked')) {
                    count--;
                    likeBtn.classList.remove('liked');
                } else {
                    count++;
                    likeBtn.classList.add('liked');
                }
                likeBtn.dataset.count = count;
                likeBtn.querySelector('span').textContent = formatNumber(count);
            });

            const bidBtn = postElement.querySelector('.bid-btn');
            bidBtn.addEventListener('click', () => {
                alert(`Place your bid for ${post.title}`);
            });

            return postElement;
        }

        function renderPosts() {
            const container = document.getElementById('post-container');
            posts.forEach(post => {
                const postElement = createPostElement(post);
                container.appendChild(postElement);
            });
        }

        document.addEventListener('DOMContentLoaded', renderPosts);
    </script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/js/all.min.js"></script>
</body>
