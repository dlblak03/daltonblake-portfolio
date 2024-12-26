<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import { dark } from '../ui_store';
</script>

<svelte:head>
	<title>Dalton Blake | Privacy Policy</title>

	<meta
		name="description"
		content="Boost your productivity with the 25+5 Method, a web tool designed to optimize work and break cycles. Track your time effectively with customizable work sessions and breaks to maintain focus and recharge throughout the day."
	/>
</svelte:head>

<Column dark={$dark} minwidth="100%" maxwidth="100%" alignitems="center">
	<div class="container {$dark ? 'dark-content' : ''}">
		<header>
			<h1>Privacy Policy</h1>
		</header>

		<section class="policy-content">
			<p><strong>Last updated: 23. December 2024</strong></p>
			<p>
				This Privacy Policy explains how Dalton Blake (“we,” “our,” or “us”) collects, uses, and
				protects your personal information when you visit our personal portfolio website
				(https://daltonblake.netlify.app/). We respect your privacy and are committed to protecting
				your personal data in accordance with applicable laws, including the General Data Protection
				Regulation (GDPR) in the EU and relevant US privacy regulations.
			</p>

			<h2>1. Information We Collect</h2>
			<p>
				We do not collect personal information (such as your name, email address, or other
				identifiable data) through this website. The website is designed to offer a smooth user
				experience, and no personal information is required to access or use it.
			</p>
			<p>However, we use two non-identifiable cookies that enhance your experience:</p>
			<ul>
				<li>
					<strong>Dark Mode Cookie:</strong> A cookie is used to store your preference for dark mode.
					This is a boolean value that indicates whether you prefer to use dark mode on the site.
				</li>
				<li>
					<strong>Language Preference Cookie:</strong> A cookie is used to store your language preference.
					This is a string value, either “EN” (English) or “DE” (German), depending on the language you
					select.
				</li>
			</ul>
			<p>These cookies are only stored in your browser and are not shared with third parties.</p>

			<h2>2. Third-Party Services</h2>
			<p>We use the following third-party services to enhance the functionality of our website:</p>
			<ul>
				<li>
					<strong>Netlify:</strong> Our website is hosted on Netlify, a platform that may process
					your data to provide hosting services. Netlify’s privacy policy can be found here:
					<a href="https://www.netlify.com/privacy/" target="_blank">Netlify Privacy Policy</a>.
				</li>
				<li>
					<strong>FontAwesome:</strong> We use FontAwesome for icons on our website. FontAwesome may
					collect information, such as IP addresses, through their service. You can review
					FontAwesome’s privacy practices here:
					<a href="https://fontawesome.com/privacy" target="_blank">FontAwesome Privacy Policy</a>.
				</li>
				<li>
					<strong>Google Fonts (Poppins):</strong> We use Google Fonts to display the Poppins font
					on our website. When you access our website, Google may collect information such as your
					IP address. You can review Google’s privacy practices here:
					<a href="https://developers.google.com/fonts/faq/privacy" target="_blank"
						>Google Privacy Policy</a
					>.
				</li>
			</ul>
			<p>
				Please note that these third-party services are separate entities, and we have no control
				over their data collection practices. We encourage you to review their privacy policies for
				more details.
			</p>

			<h2>3. Cookies</h2>
			<p>This website uses the following cookies:</p>
			<ul>
				<li>
					<strong>Dark Mode Preference Cookie:</strong> Stores a boolean value indicating whether you
					have enabled dark mode on the site. This cookie expires after 1 day and is only deleted when
					you clear your browser data.
				</li>
				<li>
					<strong>Language Preference Cookie:</strong> Stores a string value (“EN” or “DE”) that represents
					your language choice for the website. This cookie expires after 1 day and is only deleted when
					you clear your browser data.
				</li>
			</ul>
			<p>
				These cookies do not collect personal information or track you across websites. They are
				used solely to enhance your experience by remembering your preferences.
			</p>
			<p>
				You can manage or block cookies through your browser settings if you wish to do so. Please
				note that disabling cookies may affect the functionality of the site.
			</p>

			<h2>4. Data Storage and Security</h2>
			<p>
				As we do not collect personal data, we do not store any personal information on our servers.
				The cookies we use are stored only in your browser and are not shared with any third
				parties. The third-party services we use (Netlify, FontAwesome, and Google Fonts) may store
				data as part of their normal operations, but we do not have access to that data.
			</p>

			<h2>5. Your Rights</h2>
			<p>
				Under the GDPR, if you are located in the EU, you have certain rights regarding your
				personal data. These rights include:
			</p>
			<ul>
				<li>
					<strong>Right to access:</strong> You can request a copy of any personal data we may hold about
					you (though we do not collect any personal data).
				</li>
				<li>
					<strong>Right to erasure:</strong> You can request the deletion of your personal data (again,
					we do not collect any personal data).
				</li>
				<li>
					<strong>Right to rectification:</strong> You can request correction of any inaccurate or incomplete
					data (not applicable to us, as we don’t collect personal data).
				</li>
			</ul>
			<p>
				If you are located in the EU and have concerns about how your data is handled by third-party
				services, we encourage you to reach out to the relevant providers directly (Netlify,
				FontAwesome, Google Fonts).
			</p>

			<h2>6. Changes to This Privacy Policy</h2>
			<p>
				We may update this Privacy Policy from time to time. Any changes will be posted on this page
				with an updated “Last updated” date. We encourage you to review this Privacy Policy
				periodically to stay informed about how we are protecting your information.
			</p>

			<h2>7. Contact Us</h2>
			<p>If you have any questions or concerns about this Privacy Policy, please contact us at:</p>
			<ul>
				<li><strong>portfolioprivacy.rocket940@passmail.com</strong></li>
			</ul>
		</section>
	</div>
</Column>

<style>
	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 20px;
		width: calc(100% - 40px);
	}

	.dark-content * {
		color: var(--darktext) !important;
	}

	header {
		text-align: center;
		margin-bottom: 40px;
	}

	header h1 {
		font-size: 2.5em;
		color: var(--primary);
		transition: all 150ms;
	}

	.policy-content {
		padding: 20px;
		border-radius: 8px;
		transition: all 150ms;
	}

	h2 {
		color: var(--primary);
		margin-top: 20px;
		font-size: 1.8em;
		transition: all 150ms;
	}

	p {
		font-size: 1em;
		margin-bottom: 20px;
		color: var(--primary);
		transition: all 150ms;
	}

	li {
		color: var(--primary);
		transition: all 150ms;
		font-size: 1em;
	}

	/* Responsive styling */
	@media (max-width: 768px) {
		.container {
			padding: 10px;
		}

		header h1 {
			font-size: 2em;
		}

		.policy-content {
			padding: 15px;
		}

		h2 {
			font-size: 1.5em;
		}

		p {
			font-size: 0.9em;
		}

		li {
			color: var(--primary);
			transition: all 150ms;
			font-size: 0.9em;
		}
	}

	@media (max-width: 480px) {
		header h1 {
			font-size: 1.8em;
		}

		h2 {
			font-size: 1.4em;
		}

		p {
			font-size: 0.85em;
		}

		li {
			color: var(--primary);
			transition: all 150ms;
			font-size: 0.85em;
		}
	}
</style>
