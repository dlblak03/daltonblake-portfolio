<script lang="ts">
	import Column from '$lib/Column.svelte';
	import Row from '$lib/Row.svelte';

	import Header from '$lib/Text/Header.svelte';
	import Body from '$lib/Text/Body.svelte';

	import Card from '$lib/Card.svelte';
	import Collapsable from '$lib/Collapsable.svelte';
	import Dialog from '$lib/Dialog.svelte';
	import Snackbar from '$lib/Snackbar.svelte';
	import Textbox from '$lib/Textbox.svelte';
	import Time from '$lib/Time.svelte';
	import Number from '$lib/Number.svelte';
	import Date from '$lib/Date.svelte';
	import Button from '$lib/Button.svelte';
	import Icon from '$lib/Icon.svelte';
	import IconImage from '$lib/IconImage.svelte';
	import Image from '$lib/Image.svelte';

	import { dark } from '../ui_store';

	import type { PageData } from './$types';
	import { onMount } from 'svelte';

	export let data: PageData;

	var pets: any[] = [{
                petid: 1000,
                pet_name: 'Nyla',
                pet_description: 'Anatolian with greyhound',
                pet_quantity: 1,
                pet_photo: {
                    length: 0
                },
                pet_dob: '2020',
                pet_color: 'Grey with stripes',
                pet_microchip_number: '05050505',
                pet_registration: 'Registered',
                pet_feed_one: '',
                pet_feed_two: '',
                pet_feeding_food: '',
                pet_food_link: '',
                pet_type: 1,
                pets_icon: 'fa-dog'
            }];
	var pets_habitats: any[] = [];
	var petIcon = true;

	var petTypes: any[] = [
		{
			id: 1,
			name: 'Dog',
			icon: 'pets'
		},
		{
			id: 2,
			name: 'Cat',
			icon: 'cat'
		},
		{
			id: 3,
			name: 'Fish',
			icon: 'fish'
		},
		{
			id: 4,
			name: 'Small Mammal',
			icon: 'mammal'
		},
		{
			id: 5,
			name: 'Bird',
			icon: 'bird'
		},
		{
			id: 6,
			name: 'Reptile',
			icon: 'reptile'
		}
	];

	var documentStorageAccount = '';

	var displayPetFoodLinkDialog = '0';
	var petFoodLink = '';
	var petFoodLinkPetID = '';

	var displayAddHabitatLink = "0";

	var displayFindExistingHabitat = "0";

	var displayVar = '0';
	var backgroundVar = 'var(--success)';
	var messageVar = '';

	var removepetid = '';

	onMount(async () => {
		await setDocumentsAccount();
		getPetHabitats();

		reactiveUI();
	});

	const reactiveUI = async () => {
		pets = pets;
		petIcon = petIcon;
	};

	const updateLocalPet = async (petid: any, data: any) => {
		let updateIndex = pets.findIndex((p) => p.petid == petid);
		pets[updateIndex] = data;

		var filteredHabitats = JSON.parse(JSON.stringify(pets_habitats)).filter(
			(ph: { petid: any }) => ph.petid == petid
		);

		pets[updateIndex]['pets_habitats'] = filteredHabitats;
		pets[updateIndex]['pets_icon'] = petTypes.find(
			(pt) => pt.id == pets[updateIndex].pet_type
		)?.icon;

		return 1;
	};

	const getPet = async (petid: any) => {
		return pets[pets.findIndex((p) => p.petid == petid)];
	};

	const getPetHabitats = async () => {
		pets_habitats = [];
	};

	const setDocumentsAccount = async () => {
		
	};

	const addNewPet = async () => {
		pets.unshift(
            {
                petid: 1000,
                pet_name: 'Nyla',
                pet_description: 'Anatolian with greyhound',
                pet_quantity: 1,
                pet_photo: {
                    length: 0
                },
                pet_dob: '2020',
                pet_color: 'Grey with stripes',
                pet_microchip_number: '05050505',
                pet_registration: 'Registered',
                pet_feed_one: '',
                pet_feed_two: '',
                pet_feeding_food: '',
                pet_food_link: '',
                pet_type: 1,
                pets_icon: 'fa-dog'
            }
        );
        pets = [...pets];
	};

	const updatePetType = async (petid: any, pettypeid: any) => {
		
	};

	const updatePetName = async (petid: any, petname: any) => {
		
	};

	const updatePetDescription = async (petid: any, petdescription: any) => {
		
	};

	const confirmRemovePet = async (petid: any) => {
		displayVar = '1';
		backgroundVar = 'var(--warn)';
		messageVar = 'Are you sure you want to remove this pet?';

		removepetid = petid;
	};

	const cancelRemovePet = async () => {
		displayVar = '0';
		backgroundVar = 'var(--warn)';
		messageVar = '';
	};

	const removePet = async (petid: any) => {
		
	};

	const uploadPhoto = async (event: any, petid: any) => {
		var uploadThisFile = event.target?.files[0];

		
	};

	const uploadPhotoHabitat = async (event: any, petid: any) => {
		var uploadThisFile = event.target?.files[0];

		
	};

	const updatePetPhotoHabitat = async (petid: any, path: any) => {
		
	};

	const updatePetPhoto = async (petid: any, path: any) => {
		reactiveUI();
	};

	const updatePetGender = async (petid: any, gender: any) => {
		reactiveUI();
	};

	const updatePetDob = async (petid: any, dob: any) => {
		reactiveUI();
	};

	const updatePetColor = async (petid: any, color: any) => {
		reactiveUI();
	};

	const updatePetMicrochipNumber = async (petid: any, microchipnumber: any) => {
		reactiveUI();
	};

	const updatePetRegistration = async (petid: any, registration: any) => {
		reactiveUI();
	};

	const updatePetFeedingTimes = async (petid: any, feedone: any, feedtwo: any) => {
		reactiveUI();
	};

	const updatePetFood = async (petid: any, food: any) => {
		reactiveUI();
	};

	const updatePetQuantity = async (petid: any, quantity: any) => {
		reactiveUI();
	};

	const updatePetFoodLink = async (petid: any, petfoodlink: any) => {
		reactiveUI();
	};

	const viewPet = async (petid: any) => {
		var viewThisPet = await getPet(petid);

		if (viewThisPet.pet_photo.length > 0) {
			var fileBlob = await getImage(viewThisPet.pet_photo);

			if (fileBlob) {
				var fileString = URL.createObjectURL(fileBlob);
				document.getElementById('petPhoto_' + petid)?.setAttribute('src', fileString);
			}
		}
	};

	const getImage = async (path: any) => {
		

		return null;
	};

    const toggleDark = async () => {
		$dark = !$dark;
	};

	const toggleHome = async () => {
		window.location.href = '/';
	};
</script>

<Column
	background={$dark ? 'rgb(20,20,20)' : 'rgb(250,250,250)'}
	grow="1"
	minheight="100vh"
	padding="0 20px"
    overflowx="hidden"
>

<Row align="center" height="100px" gap="20px" width="100%" zindex="2">
    <Row on:click={toggleHome} cursor="pointer" borderradius="5px">
        <!-- <Image src={Main_Logo} height="75px" width="150px" borderradius="5px" alt="Ktomek Logo" /> -->
    </Row>
    <div class="tablet-above">
        <Row gap="20px">
            <!-- <Button color="{$dark ? 'var(--darktext)' : 'var(--primary)'}"><a href="/auth?type=life" class="link-a">Life</a></Button> -->
            <!-- <Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
                ><a href="/auth?type=work" class="link-a">About</a></Button
            > -->
        </Row>

        <Row marginleft="auto" gap="20px" align="center">
            <Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
                ><a href="/#about" class="link-a">About</a></Button
            >
            <Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
                ><a href="/#projects" class="link-a">Projects</a></Button
            >
            <Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
                ><a href="/#blog" class="link-a">Blog</a></Button
            >
            <Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
                ><a href="/#contact" class="link-a">Contact</a></Button
            >
            {#if $dark}
                <Row
                    on:click={toggleDark}
                    id="ui_mode"
                    marginleft="auto"
                    align="center"
                    justify="center"
                    padding="0 20px"
                    cursor="pointer"
                >
                    <Icon color="var(--darktext)" icon="fa-sun-bright" size="fa-xl" />
                </Row>
            {:else}
                <Row
                    on:click={toggleDark}
                    id="ui_mode"
                    marginleft="auto"
                    align="center"
                    justify="center"
                    padding="0 20px"
                    cursor="pointer"
                >
                    <Icon color="var(--primary)" icon="fa-moon" size="fa-xl" />
                </Row>
            {/if}
        </Row>
    </div>
    <div class="mobile-only" style="display: flex; align-items: center; gap: 10px; margin-right: 20px;">
        {#if $dark}
            <Row
                on:click={toggleDark}
                id="ui_mode"
                marginleft="auto"
                align="center"
                justify="center"
                padding="0 20px"
                cursor="pointer"
            >
                <Icon color="var(--darktext)" icon="fa-sun-bright" size="fa-xl" />
            </Row>
        {:else}
            <Row
                on:click={toggleDark}
                id="ui_mode"
                marginleft="auto"
                align="center"
                justify="center"
                padding="0 20px"
                cursor="pointer"
            >
                <Icon color="var(--primary)" icon="fa-moon" size="fa-xl" />
            </Row>
        {/if}

        <input id="menu-toggle" type="checkbox" />
        <label class="menu-button-container" for="menu-toggle">
            <div
                style="background-color: {$dark ? 'var(--darktext)' : 'var(--primary)'}"
                class="menu-button {$dark ? 'dark-menu' : 'light-menu'}"
            />
        </label>

        <ul class="menu" style="background: {$dark ? 'rgb(20,20,20)' : 'rgb(250,250,250)'}">
            <li>
                <a
                    href="/"
                    class="link-a"
                    style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Home</a
                >
            </li>
            <li>
                <a
                    href="/#about"
                    class="link-a"
                    style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">About</a
                >
            </li>
            <li>
                <a
                    href="/#projects"
                    class="link-a"
                    style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Projects</a
                >
            </li>
            <li>
                <a
                    href="/#blog"
                    class="link-a"
                    style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Blog</a
                >
            </li>
            <!-- <li><a href="/auth?type=life" class="link-a" style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Ktomek Life</a></li> -->
            <li>
                <a
                    href="/#contact"
                    class="link-a"
                    style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Contact</a
                >
            </li>
        </ul>
    </div>
</Row>

<Column borderradius="5px" background="var(--primary)" align="center" width="100%" zindex="2" padding="0 0 10px 0">
    <Body height="0px" align="center" size="24px" color={$dark ? 'var(--darktext)' : 'var(--darktext)'}
		>Pet Manager</Body
	>
	<Body align="center" size="18px" color={$dark ? 'var(--darktext)' : 'var(--darktext)'}>UI for managing pets.</Body>
</Column>

<Row grow="1" width="100%" justify="center" overflowy="auto">
	<Column minheight="0" width="100%" align="center" padding="50px 0" gap="50px">
		<Row width="100%" align="center" justify="center">
			<Button
				buttonType="success"
				on:click={addNewPet}
				width="80%"
				color={$dark ? 'var(--darktext)' : 'var(--primary)'}
				><Icon icon="fa-plus" />Add a pet</Button
			>
		</Row>

		<Row width="100%">
			<Column width="100%" padding="20px 0" gap="50px">
				{#each pets as pet}
					<Row width="100%" align="center" justify="center">
						<Card
							shadow="rgba(0, 0, 0, 0.3) 0px 4px 12px"
							background={$dark ? 'rgb(75,75,75)' : 'initial'}
							width="80%"
							maxwidth="none"
						>
							{#if pet.pet_type == 0}
								<Row width="100%" height="100%" align="center">
									<Row padding="0 30px" height="100%" align="center">
										<Body
											weight="600"
											spacing="0.2rem"
											color={$dark ? 'var(--darktext)' : 'var(--primary)'}>PET TYPE:</Body
										>
									</Row>

									<Row grow="1" gap="20px" padding="20px 0">
										{#each petTypes as petType}
											<Button
												on:click={() => {
													updatePetType(pet.petid, petType.id);
												}}
												color={$dark ? 'var(--darktext)' : 'var(--primary)'}><IconImage
												cursor="default"
												border={$dark ? 'none' : 'none'}
												background={$dark ? 'transparent' : 'transparent'}
												name={petType.icon}
												width="25px"
												height="25px"
											/>{petType.name}</Button
											>
										{/each}
									</Row>
								</Row>
							{:else}
								<Column width="100%" height="100%">
									<Row grow="1" width="100%">
										<Row align="center" grow="1" padding="40px 20px 40px 20px">
											{#if pet.pet_type == 1}
												<Row align="center">
													<Icon
														icon={pet.pets_icon}
														size="fa-xl"
                                                        color={$dark ? 'var(--darktext)' : 'var(--primary)'}
													/>
												</Row>
											{:else if pet.pet_type == 2}
												<Row>
													<IconImage
														cursor="default"
														border={$dark ? 'none' : 'none'}
														background={$dark ? 'transparent' : 'transparent'}
														name={pet.pets_icon}
														width="50px"
														height="50px"
													/>
												</Row>
											{:else if pet.pet_type == 3}
												<Row>
													<IconImage
														cursor="default"
														border={$dark ? 'none' : 'none'}
														background={$dark ? 'transparent' : 'transparent'}
														name={pet.pets_icon}
														width="50px"
														height="50px"
													/>
												</Row>
											{:else if pet.pet_type == 4}
												<Row>
													<IconImage
														cursor="default"
														border={$dark ? 'none' : 'none'}
														background={$dark ? 'transparent' : 'transparent'}
														name={pet.pets_icon}
														width="50px"
														height="50px"
													/>
												</Row>
											{:else if pet.pet_type == 5}
												<Row>
													<IconImage
														cursor="default"
														border={$dark ? 'none' : 'none'}
														background={$dark ? 'transparent' : 'transparent'}
														name={pet.pets_icon}
														width="50px"
														height="50px"
													/>
												</Row>
											{:else if pet.pet_type == 6}
												<Row>
													<IconImage
														cursor="default"
														border={$dark ? 'none' : 'none'}
														background={$dark ? 'transparent' : 'transparent'}
														name={pet.pets_icon}
														width="50px"
														height="50px"
													/>
												</Row>
											{/if}

											{#if pet.pet_type == 1 || pet.pet_type == 2 || pet.pet_type == 4 || pet.pet_type == 5 || pet.pet_type == 6}
												<Row>
													<Textbox
														dark={$dark}
														id={'petname_' + pet.petid}
														name="petname"
														bind:value={pet.pet_name}
														on:change={() => {
															updatePetName(pet.petid, pet.pet_name);
														}}>Pet name</Textbox
													>
												</Row>

												<Row grow="1">
													<Textbox
														dark={$dark}
														id={'petdescription_' + pet.petid}
														name={'petdescription_' + pet.petid}
														bind:value={pet.pet_description}
														on:change={() => {
															updatePetDescription(pet.petid, pet.pet_description);
														}}>Pet description</Textbox
													>
												</Row>
											{:else if pet.pet_type == 3}
												<Row>
													<Number
														dark={$dark}
														id={'petquantity_' + pet.petid}
														name={'petquantity_' + pet.petid}
														bind:value={pet.pet_quantity}
														on:change={() => {
															updatePetQuantity(pet.petid, pet.pet_quantity);
														}}>Pet quantity</Number
													>
												</Row>

												<Row grow="1">
													<Textbox
														dark={$dark}
														id={'petdescription_' + pet.petid}
														name={'petdescription_' + pet.petid}
														bind:value={pet.pet_description}
														on:change={() => {
															updatePetDescription(pet.petid, pet.pet_description);
														}}>Pet species</Textbox
													>
												</Row>
											{/if}

											<Row height="100%" align="center" justify="center">
												<Button
													buttonType="warn"
													on:click={() => {
														confirmRemovePet(pet.petid);
													}}
													color={$dark ? 'var(--darktext)' : 'var(--primary)'}
													width="fit-content"
													><Icon icon="fa-xmark-large" size="fa-lg" marginleft="5px" /></Button
												>
											</Row>
										</Row>
									</Row>

									<Row grow="1" width="100%">
										<Row grow="1" padding="0 20px 20px">
											<Collapsable
												on:click={() => {
													viewPet(pet.petid);
												}}
												title="View pet"
												titlecolor={$dark ? 'var(--darktext)' : 'var(--primary)'}
											>
												<Row grow="1" width="100%" wrap="wrap">
													<Row padding="20px">
														{#if pet.pet_photo.length == 0}
															<Row
																on:click={() => {
																	document.getElementById('uploadPhoto_' + pet.petid)?.click();
																}}
																align="center"
																justify="center"
																border="solid 1px var(--primary)"
																borderradius="5px"
																width="150px"
																height="150px"
																cursor="pointer"
															>
																<Icon
																	icon="fa-plus"
																	size="fa-2x"
																	color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																/>
																<input
																	type="file"
																	accept="image/*"
																	hidden
																	id={'uploadPhoto_' + pet.petid}
																	on:change={(event) => {
																		uploadPhoto(event, pet.petid);
																	}}
																/>
															</Row>
														{:else}
															<Row
																align="center"
																height="fit-content"
																border="solid 1px var(--primary)"
																borderradius="5px"
															>
																<Image
																	borderradius="5px"
																	src=""
																	alt="pet photo"
																	id={'petPhoto_' + pet.petid}
																	width="150px"
																/>
															</Row>
														{/if}
													</Row>
													{#if pet.pet_type == 1 || pet.pet_type == 2 || pet.pet_type == 4 || pet.pet_type == 5 || pet.pet_type == 6}
														<Column padding="40px 20px" gap="40px">
															<Row align="center">
																{#if pet.pet_gender == 'Male'}
																	<Row
																		padding="0 10px"
																		cursor="pointer"
																		on:click={() => {
																			updatePetGender(pet.petid, 'Female');
																		}}
																	>
																		<Icon
																			icon="fa-mars"
																			size="fa-2x"
																			color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																		/>
																	</Row>
																{:else}
																	<Row
																		padding="0 10px"
																		cursor="pointer"
																		on:click={() => {
																			updatePetGender(pet.petid, 'Male');
																		}}
																	>
																		<Icon
																			icon="fa-venus"
																			size="fa-2x"
																			color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																		/>
																	</Row>
																{/if}
																<Date
																	dark={$dark}
																	id={'petdob_' + pet.petid}
																	name={'petdob_' + pet.petid}
																	bind:value={pet.pet_dob}
																	placeholder=" "
																	on:change={() => {
																		updatePetDob(pet.petid, pet.pet_dob);
																	}}>Pet dob</Date
																>
																<Textbox
																	dark={$dark}
																	id={'petcolor_' + pet.petid}
																	name={'petcolor_' + pet.petid}
																	bind:value={pet.pet_color}
																	on:change={() => {
																		updatePetColor(pet.petid, pet.pet_color);
																	}}>Pet color</Textbox
																>
															</Row>
															{#if pet.pet_type == 1 || pet.pet_type == 2}
																<Row width="100%">
																	<Textbox
																		dark={$dark}
																		id={'petmicrochip_' + pet.petid}
																		name={'petmicrochip_' + pet.petid}
																		bind:value={pet.pet_microchip_number}
																		on:change={() => {
																			updatePetMicrochipNumber(pet.petid, pet.pet_microchip_number);
																		}}>Pet microchip #</Textbox
																	>
																</Row>
																<Row width="100%">
																	<Textbox
																		dark={$dark}
																		id={'petregistration_' + pet.petid}
																		name={'petregistration_' + pet.petid}
																		bind:value={pet.pet_registration}
																		on:change={() => {
																			updatePetRegistration(pet.petid, pet.pet_registration);
																		}}>Pet registration #</Textbox
																	>
																</Row>
															{/if}
														</Column>
													{/if}
													<Column padding="40px 20px" gap="40px">
														{#if pet.pet_type == 1 || pet.pet_type == 3}
															<Row width="100%" align="center" gap="20px">
																<Icon
																	icon="fa-utensils"
                                                                    size="fa-xl"
                                                                    color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																/>
																<Header color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																	>Feeding time #1</Header
																>
																<Time
																	dark={$dark}
																	id={'petfeedone_' + pet.petid}
																	name={'petfeedone_' + pet.petid}
																	bind:value={pet.pet_feed_one}
																	on:change={() => {
																		updatePetFeedingTimes(
																			pet.petid,
																			pet.pet_feed_one,
																			pet.pet_feed_two
																		);
																	}}>Feed</Time
																>
															</Row>
															<Row width="100%" align="center" gap="20px">
																<Icon
																	icon="fa-utensils"
                                                                    size="fa-xl"
                                                                    color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																/>
																<Header color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																	>Feeding time #2</Header
																>
																<Time
																	dark={$dark}
																	id={'petfeedtwo_' + pet.petid}
																	name={'petfeedtwo_' + pet.petid}
																	bind:value={pet.pet_feed_two}
																	on:change={() => {
																		updatePetFeedingTimes(
																			pet.petid,
																			pet.pet_feed_one,
																			pet.pet_feed_two
																		);
																	}}>Feed</Time
																>
															</Row>
														{:else if pet.pet_type == 2 || pet.pet_type == 4 || pet.pet_type == 5 || pet.pet_type == 6}
															<Row width="100%" align="center" gap="20px">
																<IconImage
																	name="dinner"
																	width="50px"
																	height="50px"
																	background="transparent"
																/>
																<Header color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																	>Feeding time</Header
																>
																<Time
																	dark={$dark}
																	id={'petfeedone_' + pet.petid}
																	name={'petfeedone_' + pet.petid}
																	bind:value={pet.pet_feed_one}
																	on:change={() => {
																		updatePetFeedingTimes(
																			pet.petid,
																			pet.pet_feed_one,
																			pet.pet_feed_two
																		);
																	}}>Feed</Time
																>
															</Row>
														{/if}

														<Row width="100%" align="center">
															<Textbox
																dark={$dark}
																id={'petfeedfood_' + pet.petid}
																name={'petfeedfood_' + pet.petid}
																bind:value={pet.pet_feeding_food}
																on:change={() => {
																	updatePetFood(pet.petid, pet.pet_feeding_food);
																}}>Pet food</Textbox
															>

															{#if pet.pet_food_link.length > 0}
																<Row
																	cursor="pointer"
																	on:click={() => {
																		displayPetFoodLinkDialog = '1';
																		document.getElementById('petfoodlink')?.focus();
																		petFoodLinkPetID = pet.petid;
																		petFoodLink = pet.pet_food_link;
																	}}
																>
																	<Button
																		buttonType="success"
																		color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																		width="fit-content"
																		><Icon icon="fa-plus" size="fa-lg" marginleft="5px" /></Button
																	>
																</Row>
															{:else}
																<Row
																	cursor="pointer"
																	on:click={() => {
																		displayPetFoodLinkDialog = '1';
																		document.getElementById('petfoodlink')?.focus();
																		petFoodLinkPetID = pet.petid;
																		petFoodLink = pet.pet_food_link;
																	}}
																>
																	<Button
																		buttonType="success"
																		color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																		width="fit-content"
																		><Icon icon="fa-plus" size="fa-lg" marginleft="5px" /></Button
																	>
																</Row>
															{/if}
														</Row>
													</Column>
													{#if pet.pet_type == 3 || pet.pet_type == 4 || pet.pet_type == 5 || pet.pet_type == 6}
														<Column padding="40px 20px" gap="40px" align="center">
															{#if pet.pets_habitats.length == 0}
																<Row on:click={() => {
																	displayAddHabitatLink = '1';
																}}>
																	<Button buttonType="success"
																	color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																	width="fit-content"><Icon icon="fa-plus" size="fa-lg" />Add habitat</Button>
																</Row>
																<Row>
																	<Header color={$dark ? 'var(--darktext)' : 'var(--primary)'}>OR</Header>
																</Row>
																<Row on:click={() => {
																	displayFindExistingHabitat = '1';
																}}>
																	<Button buttonType="success"
																	color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																	width="fit-content"><Icon icon="fa-search" size="fa-lg" />Find existing habitat</Button>
																</Row>
															{/if}
															
														</Column>
													{/if}
													<Column marginleft="auto" padding="40px 20px" gap="20px">
														<Row width="100%" justify="flex-end">
															<Button
																buttonType="primary"
																color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																width="fit-content"
																><Icon icon="fa-face-head-bandage" size="fa-lg" />Incident book</Button
															>
														</Row>

														<Row width="100%" justify="flex-end">
															<Button
																buttonType="primary"
																color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																width="fit-content"
																><Icon icon="fa-prescription" size="fa-lg" />Medication book</Button
															>
														</Row>

														<Row width="100%" justify="flex-end">
															<Button
																buttonType="primary"
																color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																width="fit-content"
																><Icon icon="fa-shield-virus" size="fa-lg" />Vaccination book</Button
															>
														</Row>

														<Row width="100%" justify="flex-end">
															<Button
																buttonType="primary"
																color={$dark ? 'var(--darktext)' : 'var(--primary)'}
																width="fit-content"
																><Icon icon="fa-hospital" size="fa-lg" />Vet Visit book</Button
															>
														</Row>
													</Column>
												</Row>
											</Collapsable>
										</Row>
									</Row>
								</Column>
							{/if}
						</Card>
					</Row>
				{/each}
			</Column>
		</Row>
	</Column>
</Row>

<Row width="100%" height="100%" align="center" justify="end">
    <Column width="100%">
        <div
            style="background: {$dark
                ? 'var(--darktext)'
                : 'var(--primary)'}; height: 1px; width: 100%;"
        />

        <Row width="100%" margintop="6px">
            <Row padding="0 50px">
                <div
                    style="background: {$dark
                        ? 'var(--darktext)'
                        : 'var(--primary)'}; height: 1px; width: 20px; transform: rotate(-45deg);"
                />
            </Row>
            <Row padding="0 50px" marginleft="auto">
                <div
                    style="background: {$dark
                        ? 'var(--darktext)'
                        : 'var(--primary)'}; height: 1px; width: 20px; transform: rotate(45deg);"
                />
            </Row>
        </Row>

        <Row width="100%" margintop="6px">
            <Row padding="0 25px">
                <div
                    style="background: {$dark
                        ? 'var(--darktext)'
                        : 'var(--primary)'}; height: 1px; width: 25vw;"
                />
            </Row>
            <Row padding="0 25px" marginleft="auto">
                <div
                    style="background: {$dark
                        ? 'var(--darktext)'
                        : 'var(--primary)'}; height: 1px; width: 25vw;"
                />
            </Row>
        </Row>
    </Column>
</Row>

<Row align="center" justify="center" gap="20px" width="100%" wrap="wrap">
    <Column align="center">
        <Row justify="center" padding="0 0 20px 0">
            <!-- svelte-ignore a11y-missing-attribute -->
            <Body color={$dark ? 'var(--darktext)' : 'var(--primary)'}>© 2022-2024 Development by Dalton Blake</Body>
        </Row>
    </Column>
</Row>

</Column>

<Snackbar scale={displayVar} background={backgroundVar}>
	<Row width="100%" align="center">
		<Row padding="0 20px">
			<Header color="white">{messageVar}</Header>
		</Row>

		<Row gap="20px" marginleft="auto" marginright="20px">
			<Button
				buttonType="warn"
				on:click={() => {
					cancelRemovePet();
				}}
				color={$dark ? 'var(--darktext)' : 'white'}
				width="fit-content">No</Button
			>
			<Button
				buttonType="warn"
				on:click={() => {
					removePet(removepetid);
				}}
				color={$dark ? 'var(--darktext)' : 'white'}
				width="fit-content">Yes</Button
			>
		</Row>
	</Row>
</Snackbar>

<Dialog
	dark={$dark}
	scale={displayPetFoodLinkDialog}
	on:click={(e) => {
		displayPetFoodLinkDialog = '0';
	}}
>
	<Row
		padding="50px 20px"
		width="300px"
		on:click={() => {
			setTimeout(function () {
				displayPetFoodLinkDialog = '1';
			}, 1);
		}}
	>
		<Textbox
			dark={$dark}
			id={'petfoodlink'}
			name={'petfoodlink'}
			bind:value={petFoodLink}
			on:change={() => {
				updatePetFoodLink(petFoodLinkPetID, petFoodLink);
			}}>Pet food link</Textbox
		>
	</Row>
</Dialog>

<Dialog
	dark={$dark}
	scale={displayAddHabitatLink}
	on:click={(e) => {
		displayAddHabitatLink = '0';
	}}
>
	<Row
		padding="50px 20px"
		width="300px"
		on:click={() => {
			setTimeout(function () {
				displayAddHabitatLink = '1';
			}, 1);
		}}
	>
		
	</Row>
</Dialog>

<Dialog
	dark={$dark}
	scale={displayFindExistingHabitat}
	on:click={(e) => {
		displayFindExistingHabitat = '0';
	}}
>
	<Row
		padding="50px 20px"
		width="300px"
		on:click={() => {
			setTimeout(function () {
				displayFindExistingHabitat = '1';
			}, 1);
		}}
	>
		
	</Row>
</Dialog>