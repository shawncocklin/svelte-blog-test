<!-- TODO: add some kind of visual decoration to separate header from rest of page -->
<!-- TODO: maybe try to get link animation to NOT snap back when no onger hovering -->

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
		font-size: clamp(5rem, 7.1vw + 3.6rem, 8rem);
		line-height: 1;
		margin-bottom: 0.25em;
	}

	nav {
		display: flex;
		justify-content: center;
	}

	a {
		position: relative;
		font-size: clamp(1.125rem, 0.9vw + 0.9rem, 1.5rem);
	}

	a:nth-of-type(2) {
		margin-inline: 2rem;
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
