<header>
	<h1>Sick Beats</h1>
	<nav>
		<a href="/">Home</a>
		<a href="/about">About</a>
		<a href="/posts">Posts</a>
	</nav>
</header>

<style>
	header {
		width: min(100% - 2rem, 60rem);
		margin-inline: auto;
		text-align: center;
		padding-block: 3rem;
	}

	h1 {
		font-family: 'Raleway', sans-serif;
		font-weight: 800;
		font-size: 5rem;
		line-height: 1;
		margin-bottom: 0.5em;
	}

	a {
		position: relative;
	}

	a:hover:after,
	a:focus:after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 1px;
		background-color: #e4e4e4;
		animation: underline 150ms linear;
	}

	@keyframes underline {
		0% {
			width: 0%;
		}
		100% {
			width: 100%;
		}
	}
</style>
