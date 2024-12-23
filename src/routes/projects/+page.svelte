<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import { onMount } from 'svelte';
	import { dark } from '../ui_store';

	const projects = [
		{
			name: '25 + 5 Method',
			description:
				'The 25+5 Method Web Tool helps you stay productive with adjustable work intervals. Set your preferred focus time (default 25 minutes) and break time (default 5 minutes), and track your progress easily. This tool encourages focus and rest, boosting productivity throughout the day.',
			tags: ['HTML', 'CSS', 'TypeScript', 'Tools'],
			link: '/projects/25+5'
		}
	];

	onMount(() => {});
</script>

<svelte:head>
	<title>Dalton Blake | Projects</title>

	<meta
		name="description"
		content="Explore a range of innovative projects by Dalton Blake, showcasing modern web development skills and creative solutions. Discover tools and applications designed to enhance productivity and user experience through cutting-edge technologies."
	/>
</svelte:head>

<Column dark={$dark} minwidth="100%" maxwidth="100%" alignitems="center">
	<div class="portfolio-container">
		<div class="projects-column" id="projectsColumn">
			{#each projects as project}
				<div class="project-card {$dark ? 'dark-card' : ''}">
					<h3>{project.name}</h3>
					<p>{project.description}</p>
					<div class="tags">
						{#each project.tags as tag}
							<span>{tag}</span>
						{/each}
					</div>
					<a href={project.link}>View Project</a>
				</div>
			{/each}
		</div>
	</div>
</Column>

<style>
	/* Portfolio Container */
	.portfolio-container {
		max-width: 1000px;
		margin: 0;
		width: 100%;
		margin-bottom: 25px;
	}

	/* Projects Column */
	.projects-column {
		display: flex;
		flex-direction: column;
		gap: 20px;
		margin-top: 20px;

		padding: 20px;

		width: calc(100% - 40px);
	}

	/* Project Card Styles */
	.project-card {
		background-color: #fff;
		padding: 20px;
		border-radius: 10px;

		border: 2px solid #ddd;
		transition: all 150ms;

		width: calc(100% - 40px);
	}

	.dark-card {
		background-color: #333;
		border: 2px solid #4c4c4c;
	}

	.project-card:hover {
		border-color: var(--primary);
		transform: translateY(-5px);
	}

	.dark-card:hover {
		border-color: var(--darktext);
	}

	/* Project Title */
	.project-card h3 {
		font-size: 1.8rem;
		color: var(--primary);
		margin-bottom: 10px;
		margin-top: 10px;
	}

	.dark-card h3 {
		color: var(--darktext);
	}

	/* Project Description */
	.project-card p {
		font-size: 1rem;
		color: #666;
		margin-bottom: 10px;
	}

	.dark-card p {
		color: #bababa;
	}

	/* Tags */
	.project-card .tags {
		margin-bottom: 25px;
		margin-top: 25px;
		margin-left: -5px;
		white-space: pre-wrap;
		display: flex;
		flex-wrap: wrap;
	}

	.project-card .tags span {
		background-color: #ddd;
		padding: 5px 10px;
		border-radius: 5px;
		font-size: 0.9rem;
		margin: 5px;
	}

	/* Link */
	.project-card a {
		font-size: 1.1rem;
		color: var(--primary);
		text-decoration: none;
		font-weight: bold;
	}

	.dark-card a {
		color: var(--darktext);
	}

	.project-card a:hover {
		text-decoration: underline;
	}

	@media (max-width: 768px) {
		.project-card h3 {
			font-size: 1.4rem; 
		}

		.project-card p {
			font-size: 0.85rem;
		}

		.project-card .tags span {
			font-size: 0.7rem;
		}

		.project-card a {
			font-size: 0.9rem; 
		}
	}

	@media (max-width: 480px) {
		h1 {
			font-size: 1.3rem; 
		}

		.project-card h3 {
			font-size: 1.2rem; 
		}

		.project-card p {
			font-size: 0.8rem;
		}

		.project-card .tags span {
			font-size: 0.7rem; 
		}

		.project-card a {
			font-size: 0.8rem; 
		}
	}
</style>
