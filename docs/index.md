# Welcome to Polygon Learn (beta)

Polygon's Learn platform is an evolving collection of resources for learning
about Polygon's technology stack and the underlying technologies that power it.
The materials are maintained by the
[Polygon Devrel team](https://polygon.technology/community/meet-the-devrel) and
the community, and serve to familiarize you with Polygon's technology and
ecosystem - from theory and concepts to practical examples.

As this platform is in its beta phase, it will be rapidly evolving. While we
strive to provide accurate and up-to-date information, some mistakes and
outdated content may appear. Rest assured, these will be promptly addressed as
we continue to improve and expand the platform.

## Community Contributions

We highly encourage contributions from the community. Your input is invaluable
in making this the ultimate repository of Polygon-related knowledge. By
contributing, you not only help others but also get recognized on our
contributor list. Exceptional contributions may even result in financial
incentives. For more details on how to contribute and claim topics, please
consult the [README](https://github.com/0xPolygon/devrel-docs).

We are committed to making Polygon Learn the definitive source of knowledge for
Polygon's technology and ecosystem. This platform is designed to grow and
improve with the help of our community, ensuring that it remains a reliable and
comprehensive resource.

## Where to begin

Start by learning the basics about the key concepts of Polygon's technology:

- [AggLayer](agglayer/overview.md)
- [Polygon PoS](pos/overview.md)
- [Polygon zkEVM](zkevm/overview.md)
- [Polygon Miden](miden/overview.md)
- [Polygon CDK](cdk/overview.md)
- [Polygon Plonky3](plonky3/overview.md)

If you'd like to learn more about general web3 terms and concepts, check out our
friends at [Dabl Club](https://dabl.club) instead - they offer a solid
foundation of knowledge which can be significantly augmented with the more
domain-specific knowledge in this platform.

## Contributors

<style>
.contributor-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin-top: 30px;
}

.contributor-card {
    background-color: #f5f5f5;
    border-radius: 8px;
    padding: 20px;
    width: 250px;
    min-width: 200px;
    max-width: 300px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
}

.contributor-card img {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin-bottom: 10px;
}

.contributor-card h3 {
    margin: 0 0 10px 0;
}
.contributor-card a {
    display: inline-block;
    margin: 5px;
    color: #333;
    text-decoration: none;
    font-size: 24px;
}

.contributor-card a:hover {
    opacity: 0.7;
}

.contributor-card .material-icons {
    font-size: 24px;
}

.telegram-icon {
    display: inline-block;
    width: 24px;
    height: 24px;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24'%3E%3Cpath fill='currentColor' d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10s10-4.48 10-10S17.52 2 12 2m4.64 6.8c-.15 1.58-.8 5.42-1.13 7.19c-.14.75-.42 1-.68 1.03c-.58.05-1.02-.38-1.58-.75c-.88-.58-1.38-.94-2.23-1.5c-.99-.65-.35-1.01.22-1.59c.15-.15 2.71-2.48 2.76-2.69a.2.2 0 0 0-.05-.18c-.06-.05-.14-.03-.21-.02c-.09.02-1.49.95-4.22 2.79c-.4.27-.76.41-1.08.4c-.36-.01-1.04-.2-1.55-.37c-.63-.2-1.12-.31-1.08-.66c.02-.18.27-.36.74-.55c2.92-1.27 4.86-2.11 5.83-2.51c2.78-1.16 3.35-1.36 3.73-1.36c.08 0 .27.02.39.12c.1.08.13.19.14.27c-.01.06.01.24 0 .38'/%3E%3C/svg%3E");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
}

.github-icon {
    display: inline-block;
    width: 24px;
    height: 24px;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24'%3E%3Cpath fill='currentColor' d='M12.001 2c-5.525 0-10 4.475-10 10a9.99 9.99 0 0 0 6.837 9.488c.5.087.688-.213.688-.476c0-.237-.013-1.024-.013-1.862c-2.512.463-3.162-.612-3.362-1.175c-.113-.288-.6-1.175-1.025-1.413c-.35-.187-.85-.65-.013-.662c.788-.013 1.35.725 1.538 1.025c.9 1.512 2.337 1.087 2.912.825c.088-.65.35-1.087.638-1.337c-2.225-.25-4.55-1.113-4.55-4.938c0-1.088.387-1.987 1.025-2.687c-.1-.25-.45-1.275.1-2.65c0 0 .837-.263 2.75 1.024a9.3 9.3 0 0 1 2.5-.337c.85 0 1.7.112 2.5.337c1.913-1.3 2.75-1.024 2.75-1.024c.55 1.375.2 2.4.1 2.65c.637.7 1.025 1.587 1.025 2.687c0 3.838-2.337 4.688-4.562 4.938c.362.312.675.912.675 1.85c0 1.337-.013 2.412-.013 2.75c0 .262.188.574.688.474A10.02 10.02 0 0 0 22 12c0-5.525-4.475-10-10-10'/%3E%3C/svg%3E");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
}

.twitter-icon {
    display: inline-block;
    width: 24px;
    height: 24px;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='14' height='14' viewBox='0 0 14 14'%3E%3Cg fill='none'%3E%3Cg clip-path='url(%23primeTwitter0)'%3E%3Cpath fill='currentColor' d='M11.025.656h2.147L8.482 6.03L14 13.344H9.68L6.294 8.909l-3.87 4.435H.275l5.016-5.75L0 .657h4.43L7.486 4.71zm-.755 11.4h1.19L3.78 1.877H2.504z'/%3E%3C/g%3E%3Cdefs%3E%3CclipPath id='primeTwitter0'%3E%3Cpath fill='%23fff' d='M0 0h14v14H0z'/%3E%3C/clipPath%3E%3C/defs%3E%3C/g%3E%3C/svg%3E");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
}
</style>

<div class="contributor-grid">
    <div class="contributor-card">
        <img src="https://github.com/swader.png" alt="Bruno Skvorc">
        <h3><a href="https://github.com/swader">Bruno Skvorc</a></h3>
        <a href="https://github.com/swader"><span class="github-icon"></span></a>
        <a href="https://x.com/bitfalls"><span class="twitter-icon"></span></a>
        <a href="https://t.me/swader"><span class="telegram-icon"></span></a>
    </div>
    <div class="contributor-card">
        <img src="https://github.com/BrianSeong99.png" alt="Brian Seong">
        <h3><a href="https://github.com/BrianSeong99">Brian Seong</a></h3>
        <a href="https://github.com/BrianSeong99"><span class="github-icon"></span></a>
        <a href="https://x.com/BrianSeong99"><span class="twitter-icon"></span></a>
        <a href="https://t.me/BrianSeong99"><span class="telegram-icon"></span></a>
    </div>
    <div class="contributor-card">
        <img src="https://github.com/gubloon.png" alt="Gubloon">
        <h3><a href="https://github.com/gubloon">Gubloon</a></h3>
        <a href="https://github.com/gubloon"><span class="github-icon"></span></a>
        <a href="https://x.com/gubloon"><span class="twitter-icon"></span></a>
        <a href="https://t.me/gubloon"><span class="telegram-icon"></span></a>
    </div>
</div>
