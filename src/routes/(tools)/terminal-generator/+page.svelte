<script lang="ts">
	import Intro from '$lib/Intro.svelte';
	import {
		Label,
		Input,
		Range,
		Radio,
		Checkbox,
		ButtonGroup,
		Button,
		Search,
		Dropdown,
		DropdownItem,
		DropdownDivider
	} from 'flowbite-svelte';

	import { onMount } from 'svelte';

	import {
		ChevronDownSolid,
		UserRemoveSolid,
		UserCircleSolid,
		AdjustmentsVerticalOutline,
		DownloadSolid,
		CopySolid,
		UserSettingsOutline,
		UserSettingsSolid
	} from 'flowbite-svelte-icons';

	import CodeMirror from 'svelte-codemirror-editor';
	import { javascript } from '@codemirror/lang-javascript';
	import { oneDark } from '@codemirror/theme-one-dark';

	export let data;

	let innerWidth: any = null;
	let innerHeight: any = null;

	let value = '';

	onMount(() => {
		// const codeEditor = document.querySelector('.code-editor');

		// if (codeEditor) {
		// 	editor = CodeMirror(codeEditor, {
		// 		lineNumbers: true,
		// 		theme: 'dracula'
		// 		// ... any other CodeMirror options you want
		// 	});
		// }

		innerWidth = window.innerWidth;
		innerHeight = window.innerHeight;
	});

	let event;
	let codeMirrorInstance: any = null;

	// function handleKeydown(event) {
	// 	if (event.keyCode === 8) {
	// 		// If the key is backspace
	// 		const cm = event.target.CodeMirror;
	// 		const cursor = cm.getCursor();
	// 		if (cursor.ch === 0 && cursor.line === 0) {
	// 			event.preventDefault();
	// 		}
	// 	}
	// }
</script>

<!--  Introduction  -->

<Intro heading={data.meta.title} description={data.meta.description} />
<!--or-->
<!-- <section class="bg-custom-white dark:bg-gray-900">
	<div class="py-8 px-4 mx-auto max-w-screen-xl text-center lg:px-12">
		<h1
			class="mb-4 text-4xl font-extrabold tracking-tight leading-none text-gray-900 dark:text-white"
		>
			Terminal Generator
		</h1>
		<p class="text-lg font-normal text-gray-500 lg:text-xl sm:px-16 xl:px-48 dark:text-gray-400">
			Create and share beautiful images of your source code. <br />
			Start typing or drop a file into the text area to get started.
		</p>
	</div>
</section> -->

<svelte:window bind:innerWidth bind:innerHeight />

<!-- Terminal -->

<section class="bg-custom-white dark:bg-gray-900">
	<div class="page py-8 px-4 mx-auto max-w-screen-xl lg:px-12">
		<div class="editor min-h-[35rem] md:w-4/5 lg:w-full rounded-lg mx-auto flex flex-col p-2">
			<!-- Toolbar Section  -->
			<div class="toolbar flex flex-wrap justify-between mb-4">
				<!-- Themes & Languages Dropdown -->
				<!-- <div class="flex space-x-4"> -->
				<div class="theme">
					<span>Theme</span>
					<!-- <span
						style="clip:rect(0 0 0 0);margin:-1px;overflow:hidden;padding:0;position:absolute;width:1px;white-space:nowrap;word-wrap:normal"
						id="theme-dropdown">Theme</span> -->
					<span class="ml-auto" />
					<ChevronDownSolid class="w-3 h-3 text-white dark:text-white" />

					<Dropdown class="overflow-y-auto px-3 pb-3 text-sm h-44 z-index: 9999">
						
						<div slot="header" class="p-3">
							<Search size="md" />
						</div>
						<DropdownItem>Aptos</DropdownItem>
						<DropdownDivider />
						<DropdownItem>Calibri</DropdownItem>
						<DropdownDivider />
						<DropdownItem>Sans serif</DropdownItem>
						<!-- <DropdownItem slot="footer">Separated link</DropdownItem> -->
					</Dropdown>
				</div>

				<div class="language">
					<span>Language</span>
					<span class="ml-auto" />
					<ChevronDownSolid class="w-3 h-3 text-white dark:text-white" />

					<Dropdown class="overflow-y-auto px-3 pb-3 text-sm h-44">
						<div slot="header" class="p-3">
							<Search size="md" />
						</div>
						<DropdownItem>C++</DropdownItem>
						<DropdownDivider />
						<DropdownItem>Java</DropdownItem>
						<DropdownDivider />
						<DropdownItem>Python</DropdownItem>
						<!-- <DropdownItem slot="footer">Separated link</DropdownItem> -->
					</Dropdown>
				</div>
				<!-- Second Toolbar Row -->
				<div class="toolbar-second-row">
					<div class="setting-buttons">
						<!-- <div class="flex space-x-4"> -->
						<!-- bg-select -->
						<div class="icon">
							<Button>
								<img src="/color-palatte.png" alt="Your  Description" />
							</Button>
						</div>
						<!-- Setting -->
						<div class="icon">
							<Button>
								<img src="/setting.png" alt="Your  Description" />
							</Button>
						</div>
						<!-- Copy-Menu -->
						<div class="icon">
							<Button>
								<img src="/copy.png" alt="Your  Description" />
							</Button>
						</div>
						<!-- Save Button -->
						<!-- <div class="save ml-auto">
							<span>Save</span>
							<span class="ml-auto" />
							<ChevronDownSolid class="w-3 h-3 text-white dark:text-white" />

						<Dropdown class="overflow-y-auto px-3 pb-3 text-sm h-44">
							<DropdownItem>Jpg</DropdownItem>
							<DropdownDivider />
							<DropdownItem>Png</DropdownItem>
							<DropdownDivider />
							<DropdownItem>Psd</DropdownItem>
							<Dropdown> -->
					</div>
					<div id="style-editor-button" class="jsx" />
					<div class="share-buttons">
						<div class="export-menu">
							<div class="id flex">
								<div class="post ml-auto">
									<span>Post</span>
									<span class="ml-auto" />
									<ChevronDownSolid class="w-3 h-3 text-white dark:text-white" />

									<Dropdown class="overflow-y-auto px-3 pb-3 text-sm h-44">
										<DropdownItem>Facebook</DropdownItem>
										<DropdownDivider />
										<DropdownItem>Instagram</DropdownItem>
										<DropdownDivider />
										<DropdownItem>Twitter</DropdownItem>
										<!-- <DropdownItem slot="footer">Separated link</DropdownItem> -->
									</Dropdown>
								</div>
							</div>
						</div>
						<!-- 
					<div class="icon">
						<Button>
							<img src="/Texttospeech.png" alt="Your  Description" />
						</Button>
					</div> -->
						<div class="export ml-auto">
							<span>Export</span>
							<span class="ml-auto" />
							<ChevronDownSolid class="w-3 h-3 text-white dark:text-white" />

							<Dropdown class="overflow-y-auto px-3 pb-3 text-sm h-44">
								<DropdownItem>Code</DropdownItem>
								<DropdownDivider />
								<DropdownItem>1 mb</DropdownItem>
								<DropdownDivider />
								<DropdownItem>Export</DropdownItem>
								<!-- <DropdownItem slot="footer">Separated link</DropdownItem> -->
							</Dropdown>
						</div>
					</div>
				</div>
			</div>
			<!-- Terminal Area (or the Code Area) -->

			<div class="terminal relative rounded-md">
				<div class="dnd-container">
					<div class="section">
						<div class="export-container">
							<div class="container">
								<!-- <div class="Windows Controls"></div> -->
								<div class="react-codemirror2 CodeMirror__container window-theme__none">
									<div class="CodeMirror cm-s-base16-dark CodeMirror-wrap" translate="no">
										<div class="CodeMirror-scrollbar-filler" />
										<div class="CodeMirror-gutter-filler" />
										<div class="CodeMirror-scroll" tabindex="-1">
											<div
												class="CodeMirror-sizer"
												style="	 margin-left: 0px; margin-bottom: 0px; border-right-width: px; min-height: 27px; padding-right: 0px; padding-bottom: 0px;"
											>
												<div style="position: relative; top: 0px;">
													<div class="terminal-header">
														<!-- <span class="mr-auto ml-2"></span> -->
														<!-- <button class="close-btn bg-red-500 rounded-full w-4 h-4 mr-1" /> -->
														<button class="close-btn" />
														<!-- <button class="minimize-btn bg-yellow-500 rounded-full w-4 h-4 mr-1" /> -->
														<button class="minimize-btn" />
														<!-- <button class="maximize-btn bg-green-500 rounded-full w-4 h-4" /> -->
														<button class="maximize-btn" />
													</div>
													<div class="CodeMirror-lines" role="presentation">
														<div role="presentation" style="position: relative; outline: none;">
															<div
																class="CodeMirror-code"
																role="presentation"
																contenteditable="true"
																autocorrect="off"
																autocapitalize="off"
																style="text-rendering: auto;"
															>
																<CodeMirror
																	bind:value
																	lang={javascript()}
																	styles={{
																		'&': {
																			width: '100%',
																			maxWidth: '100%',
																			height: '250px',
																			borderRadius: '0px',
																			margin: '0 auto'
																		}
																	}}
																	theme={oneDark}
																/>
															</div>
														</div>
													</div>
												</div>
											</div>
										</div>
									</div>
								</div>
								<div class="container-bg">
									<div class="container-bg white eliminateOnRender" />
									<div class="container-bg alpha eliminateOnRender" />
									<div class="container-bg bg" />
								</div>
								<div class="handler" />
							</div>
						</div>
					</div>
				</div>
				<!-- <textarea>Terminal</textarea> -->
				<!-- The actual terminal or code content would go here -->
			</div>
		</div>
	</div>
</section>

<style>
	.toolbar-second-row {
		/* display: flex;
		align-items: center;
		justify-content: flex-start; */
		display: -webkit-box;
		display: -webkit-flex;
		display: -moz-box;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-flex: 1;
		-webkit-flex: 1 1 auto;
		-moz-box-flex: 1;
		-ms-flex: 1 1 auto;
		flex: 1 1 auto;
	}

	:is(.dark .card) {
		box-shadow: rgba(255, 255, 255, 0.5) 0 0 0 2px;
	}

	.toolbar {
		display: flex;
		align-items: center;
	}

	.theme {
		position: relative;
		display: flex;
		align-items: center;
		justify-content: flex-start;
		border: 1px solid white;
		width: 120px;
		padding: 5px 20px;
		margin-right: 8px;
		margin-left: 9px;
		margin-top: 5px;
		border-radius: 10px;
		font-size: 15px;
		color: white;
	}

	.language {
		display: flex;
		align-items: center;
		justify-content: flex-start;
		border: 1px solid white;
		width: 150px;
		padding: 5px 25px;
		margin-left: 0.5px;
		margin-right: 8px;
		margin-top: 5px;
		border-radius: 10px;
		font-size: 15px;
		color: white;
	}

	#style-editor-button.jsx {
		display: -webkit-box;
		display: -webkit-flex;
		display: -moz-box;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-align: center;
		-webkit-align-items: center;
		-moz-box-align: center;
		-ms-flex-align: center;
		align-items: center;
	}

	.share-buttons {
		margin-left: auto;
	}

	.share-buttons,
	.setting-buttons {
		display: -webkit-box;
		display: -webkit-flex;
		display: -moz-box;
		display: -ms-flexbox;
		display: flex;
		height: 40px;
	}
	.export-menu {
		position: relative;
		color: #c198fb;
		-webkit-box-flex: 1;
		-webkit-flex: 1;
		-moz-box-flex: 1;
		-ms-flex: 1;
		flex: 1;
	}
	.flex {
		display: -webkit-box;
		display: -webkit-flex;
		display: -moz-box;
		display: -ms-flexbox;
		display: flex;
		height: 100%;
	}

	.post {
		display: flex;
		align-items: center;
		justify-content: flex-start;
		border: 1px solid white;
		width: 120px;
		padding: 5px 30px;
		margin-right: 8px;
		margin-top: 5px;
		margin-left: 0.5px;
		border-radius: 10px;
		font-size: 15px;
		color: white;
	}

	.export {
		display: flex;
		align-items: center;
		justify-content: flex-start;
		border: 1px solid white;
		width: 120px;
		padding: 5px 20px;
		margin-right: 9px;
		margin-top: 5px;
		margin-left: 0.5px;
		border-radius: 10px;
		font-size: 15px;
		color: white;
	}

	.icon img {
		width: 30px;
		height: 26px;
		object-fit: cover;
	}

	.icon {
		display: flex;
		align-items: center;
		margin-right: 3px;
		margin-top: 5px;
		border-radius: 10px;
		color: white;
		background-color: #2d3748;
	}

	.dark .icon {
		background-color: #2d3748; /* Dark Mode Background Color */
	}

	.editor {
		background-color: #121212;
		border: white 2px solid;
		width: 100%;
		height: 100%;
		max-width: 800px;
	}

	.terminal {
		/* flex-grow: 1; Let the terminal consume all remaining vertical space */
		width: 800px;
		height: calc(100% - 4rem); /* Assuming 4rem is the height of your toolbar, adjust as needed */
		display: flex;
		/* flex-direction: column; */
		margin: 0 auto;
	}

	.bg {
		background-color: #121212;
		border: white 2px solid;
		display: flex; /* Set the container to use Flexbox */
		flex-direction: column; /* Arrange children (toolbar & terminal) vertically */
		height: 100%; /* If you want it to fill the height of its parent */
	}

	.dnd-container {
		position: relative;
		flex-grow: 1; /* This makes the code container grow to take all available space */
	}

	.section,
	.export-container {
		height: 100%;
		display: -webkit-box;
		display: -webkit-flex;
		display: -moz-box;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-orient: vertical;
		-webkit-box-direction: normal;
		-webkit-flex-direction: column;
		-moz-box-orient: vertical;
		-moz-box-direction: normal;
		-ms-flex-direction: column;
		flex-direction: column;
		-webkit-box-pack: center;
		-webkit-justify-content: center;
		-moz-box-pack: center;
		-ms-flex-pack: center;
		justify-content: center;
		-webkit-box-align: center;
		-webkit-align-items: center;
		-moz-box-align: center;
		-ms-flex-align: center;
		align-items: center;
		overflow: hidden;
		max-width: 100%;
	}

	/* @media (max-width: 768px) */
	.container {
		/* max-width: 480px; */
		position: relative;
		min-width: 400px;
		max-width: 700px;
		width: auto;
		height: auto;

		padding: 56px 56px;
	}

	.container .CodeMirror__container {
		min-width: inherit;
		position: relative;
		z-index: 1;
		-webkit-border-radius: 5px;
		-moz-border-radius: 5px;
		border-radius: 5px;
		box-shadow: 0 20px 68px rgba(0, 0, 0, 0.55);
	}

	.container .CodeMirror__container .CodeMirror {
		height: auto;
		background-color: #282c34;
		color: #abb2bf;
		min-width: inherit;
		padding: 5px 5px;
		padding-left: 5px;
		border-radius: 5px;
		font-family: Hack, monospace !important;
		font-size: 14px;
		line-height: 133%;
		-webkit-font-variant-ligatures: contextual;
		-moz-font-variant-ligatures: contextual;
		font-variant-ligatures: contextual;
		-webkit-font-feature-settings: 'calt' 1;
		-moz-font-feature-settings: 'calt' 1;
		font-feature-settings: 'calt' 1;
		-webkit-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
		-webkit-tap-highlight-color: transparent;
		outline: none;
	}

	.CodeMirror-gutter-filler,
	.CodeMirror-scrollbar-filler {
		position: absolute;
		z-index: 6;
		display: none;
		outline: 0;
	}

	.CodeMirror-gutter-filler,
	.CodeMirror-scrollbar-filler {
		background-color: #fff;
	}

	.container-bg {
		position: absolute;
		top: 0px;
		right: 0px;
		bottom: 0px;
		left: 0px;
	}

	.container-bg .white {
		background: #fff;
		position: absolute;
		top: 0px;
		right: 0px;
		bottom: 0px;
		left: 0px;
	}

	.container-bg .alpha {
		position: absolute;
		top: 0px;
		right: 0px;
		bottom: 0px;
		left: 0px;
		/* background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAMUlEQVQ4T2NkYGAQYcAP3uCTZhw1gGGYhAGBZIA/nYDCgBDAm9BGDWAAJyRCgLaBCAAgXwixzAS0pgAAAABJRU5ErkJggg==); */
	}

	.container-bg .bg {
		background: rgb(116, 116, 116);
		background-size: auto;
		background-repeat: repeat;
		position: absolute;
		top: 0px;
		right: 0px;
		bottom: 0px;
		left: 0px;
	}

	.handler {
		z-index: 2;
		position: absolute;
		background-color: #8c104e;
		top: 56px;
		bottom: 56px;
		right: 56px;
		width: 8px;
		cursor: ew-resize;
		opacity: 0;
	}

	.terminal-header {
		display: flex;
		align-items: center;
		border-radius: 0px;

		background-color: #282c34; /* One Dark background color */
		color: #abb2bf; /* One Dark foreground color */
		/* border-bottom: 1px solid #3e4451; Slight border to separate from the terminal content */
	}

	.close-btn,
	.minimize-btn,
	.maximize-btn {
		margin: 2px;
		cursor: pointer;
		transition: background-color 0.2s;
		width: 12px;
		height: 12px;
		border-radius: 50%;
	}

	.close-btn {
		background-color: #e06c75; /* One Dark red color */
	}

	.minimize-btn {
		background-color: #d19a66; /* One Dark yellow color */
	}

	.maximize-btn {
		background-color: #98c379; /* One Dark green color */
	}

	.close-btn:hover {
		background-color: darken(#e06c75, 10%); /* Slightly darken on hover */
	}

	.minimize-btn:hover {
		background-color: darken(#d19a66, 10%);
	}

	.maximize-btn:hover {
		background-color: darken(#98c379, 10%);
	}

	Dropdown {
		z-index: 9999; /* Some high value to ensure it's on top of other elements */
		/* position: relative; Ensures z-index applies */
	}
</style>