// Initialize step and character data
let step = 0;  // Start from Step 0 to show the Character Concept first
let redistributionPool = 0;
const character = {
    concept: '',
    traits: [],
    childhood: {},
    education: {},
    hobbies: {},
    job: {},
    after: {},
    complicationsAndMotivations: {},
    totals: {
        attributes: { reason: 0, acumen: 0, physicality: 0, influence: 0, dexterity: 0 },
        skills: {}
    }
};

// Arrays of sample names and professions
const firstNames = [
    "Alex", "Morgan", "Jordan", "Taylor", "Casey", "Jamie", "Reese", "Quinn", 
    "Riley", "Avery", "Cameron", "Dakota", "Skylar", "Harper", "Rowan",
    "Emerson", "Sage", "Finley", "Logan", "Blake", "Phoenix", "Hunter", "Peyton", 
    "Charlie", "Elliot", "Jesse", "Parker", "Tatum", "Bailey", "River", 
    "Remy", "Sawyer", "Reagan", "Lennon", "Hayden", "Dallas", "Chandler", 
    "Kendall", "Micah", "Justice", "Rory", "Frankie", "Sloan", "Drew", 
    "Spencer", "Morgan", "Dakota", "Blair", "Morgan", "Jayden", "Hollis",
    // Additional international/ethnic names
    "Amari", "Ravi", "Sami", "Lian", "Niko", "Keiko", "Anil", "Yara", 
    "Sorin", "Leila", "Amina", "Inez", "Davi", "Suri", "Hadi", 
    "Mira", "Aziz", "Noor", "Omar", "Akira", "Tariq", "Luca", 
    "Zara", "Indra", "Rina", "Anaya", "Jalen", "Nadia", "Kazuo", 
    "Sasha", "Shirin", "Raj", "Tala", "Miguel", "Elif", "Vanya", 
    "Diego", "Eliya", "Fatima", "Idris", "Jun", "Meera", "Sofia", 
    "Aliyah", "Dimitri", "Hasan", "Lucia", "Eshan", "Kiran", "Samir"
];

const lastNames = [
    "Carter", "Brooks", "Hunter", "Bailey", "Rivers", "Monroe", "Blake", 
    "Jordan", "Maxwell", "Porter", "Taylor", "Morgan",
    // Additional names
    "Sutton", "Griffin", "Bennett", "Hayes", "Kennedy", "Reed", "Parker", 
    "Fletcher", "Hale", "Mason", "Lawson", "Collins", "Sullivan", "Bishop", 
    "Hudson", "Wells", "Cooper", "Anderson", "Bradley", "Spencer", "Cole", 
    "Reese", "Carson", "Tucker", "Grant", "Chandler", "Murphy", "West", 
    "Davis", "Adler", "Logan", "Keller", "Fox", "Nelson", "Finch",
    // International/ethnic names
    "Patel", "Chen", "Diaz", "Khan", "Nguyen", "Ali", "Garcia", "Kim", 
    "Singh", "Hernandez", "Sato", "López", "Yamada", "Das", "Hassan", 
    "Mendoza", "Bakir", "Morales", "Ochoa", "Amari", "Ibrahim", "Chang", 
    "Okoro", "Rossi", "Leclerc", "Santana", "Ortega", "Kuroda", "Matsumoto", 
    "Liu", "Salim", "Rahman", "Silva", "Moreau", "Ahmed", "Nasser", 
    "Cruz", "Mohammed", "Fernandez", "Ishikawa", "Novak", "Jafari", 
    "Almeida", "Rizvi", "Tanaka", "Duarte", "Abebe", "Espinoza", "Omar", 
    "Pereira", "Santos", "Miyamoto", "Chavez"
];

const professions = [
    "Doctor", "Farmer", "School Teacher", "Watch Maker", "Cook", 
    "Hairdresser", "Engineer", "Mechanic", "Nurse", "Police Officer",
    // Additional professions
    "Carpenter", "Blacksmith", "Electrician", "Architect", "Plumber", 
    "Pilot", "Chef", "Paramedic", "Librarian", "Firefighter", 
    "Scientist", "Artist", "Journalist", "Bartender", "Software Developer", 
    "Veterinarian", "Biologist", "Psychologist", "Therapist", "Pharmacist", 
    "Social Worker", "Construction Worker", "Baker", "Butcher", "Accountant", 
    "Lawyer", "Real Estate Agent", "Dentist", "Gardener", "Tailor", 
    "Photographer", "Musician", "Barista", "Graphic Designer", "Translator",
    "Surveyor", "Jeweler", "Geologist", "Environmental Scientist", "Meteorologist", 
    "Biotechnologist", "Chemist", "Marine Biologist", "Archaeologist", "Ecologist"
];

// Skill configuration for specific rules with base attributes
const asteriskSkills = { demolitions: -3, mechanic: -3, medicine: -3, psychology: -3, tactics: -3 };
const skillOptionsHTML = `
    <option value="Animal_Handling (INF)">Animal Handling (INF)</option>
    <option value="Athletics (PHY)">Athletics (PHY)</option>
    <option value="Barter (ACU)">Barter (ACU)</option>
    <option value="Demolitions (PHY)">Demolitions* (PHY)</option>
    <option value="Driving (DEX)">Driving (DEX)</option>
    <option value="Farming (ACU)">Farming (ACU)</option>
    <option value="General_Knowledge (RSN)">General Knowledge (RSN)</option>
    <option value="Inspiration (INF)">Inspiration (INF)</option>
    <option value="Intimidation (INF)">Intimidation (INF)</option>
    <option value="Manipulation (INF)">Manipulation (INF)</option>
    <option value="Mechanic (RSN)">Mechanic* (RSN)</option>
    <option value="Medicine (RSN)">Medicine* (RSN)</option>
    <option value="Melee_Combat (PHY)">Melee Combat (PHY)</option>
    <option value="Navigation (ACU)">Navigation (ACU)</option>
    <option value="Psychology (INF)">Psychology* (INF)</option>
    <option value="Ranged_Combat (DEX)">Ranged Combat (DEX)</option>
    <option value="Research (RSN)">Research (RSN)</option>
    <option value="Scavenging (ACU)">Scavenging (ACU)</option>
    <option value="Sleight_of_Hand (DEX)">Sleight of Hand (DEX)</option>
    <option value="Stealth (PHY)">Stealth (PHY)</option>
    <option value="Survival (ACU)">Survival (ACU)</option>
    <option value="Tactics (RSN)">Tactics* (RSN)</option>
    <option value="Tinkerer (DEX)">Tinkerer (DEX)</option>
    <option value="Unarmed_Combat (PHY)">Unarmed Combat (PHY)</option>
`;

function formatText(text) {
    return text.replace(/_/g, ' ');
}

// Initialize the process by showing the intro page
function showIntroPage() {
    const container = document.getElementById('step-container');
    container.innerHTML = `
        <h2>Welcome to the Distemper Backstory Generator</h2>
        <p>You will be guided through the various stages of your Character's life where you assign Character Development Points (CDP) to your RAPID Range Attributes and Skills.</br>
        This allows you to define what your character learned as they grew, building a character that exactly matches your vision.</p>
        <button id="start-button">Start Background Generation</button>
        <button id="random-button">Generate a Random Character</button>
    `;
    console.log("Intro page displayed.");

    // Add event listeners for the buttons
    document.getElementById("start-button").addEventListener("click", startCharacterCreation);
    document.getElementById("random-button").addEventListener("click", generateRandomCharacter);
}

// Start the character creation process from Step 1
function startCharacterCreation() {
    console.log("Starting character creation...");
    step = 0;  // Reset step to 0
    nextStep();  // Advance to first character concept step
}

// Generate random character data
function generateRandomCharacter() {
    console.log("Generating random character...");
    
    // Randomly select a name and profession
    const firstName = firstNames[Math.floor(Math.random() * firstNames.length)];
    const lastName = lastNames[Math.floor(Math.random() * lastNames.length)];
    const profession = professions[Math.floor(Math.random() * professions.length)];
    
    // Assign the random name and profession to the character object
    character.name = `${firstName} ${lastName}`;
    character.profession = profession;

    // Randomly generate age between 18 and 65
    character.age = Math.floor(Math.random() * (65 - 18 + 1)) + 18;

    // Randomly select gender with specified probabilities
    const genderRoll = Math.random();
    if (genderRoll < 0.45) {
        character.gender = "Male";
    } else if (genderRoll < 0.9) {
        character.gender = "Female";
    } else if (genderRoll < 0.95) {
        character.gender = "Nonbinary";
    } else {
        character.gender = "Gender Fluid";
    }

    // Randomly select concept, traits, complication, and motivation
    const concepts = [
        "Hardened Frontline Veteran",
        "Scavenging Urban Scholar",
        "Survivor of Countless Losses",
        "Nomad of the Broken Roads",
        "Defender of the Last Sanctuary",
        "Cunning Deal-Maker",
        "Leader Through Dark Times",
        "Edge-Seeking Wanderer",
        "Lurker in Shadows",
        "Rebel with Nothing Left to Lose",
        "Silent, Haunted Witness",
        "Keeper of Forgotten Knowledge",
        "Cold-Eyed Strategist",
        "Relentless Harbinger of Justice",
        "Visionary in Ashen Times",
        "Tracker of the Fallen",
        "Salvage Artisan",
        "Hermit of the Wastes",
        "Grim Negotiator",
        "Outlaw with a Code",
        "Protector of the Weak and Broken",
        "Field Medic of the Ruins",
        "Hunter of Lost Supplies",
        "Follower with a Quiet Loyalty",
        "Scavenger with Quick Feet",
        "Lone Survivor",
        "Dealer in Scavenged Goods",
        "Unyielding Barrier",
        "Mistrustful Trickster",
        "Healer with a Heavy Heart",
        "Relentless Seeker",
        "Master of Disappearances",
        "Watcher in the Dark",
        "Weathered Veteran",
        "Survivor of the Unpredictable",
        "Reluctant Idealist",
        "Forager in the Ruins",
        "Grit-Driven Fighter",
        "Cunning Night Raider",
        "Streetwise Haggle-Master",
        "Worn-Down Fixer",
        "Vengeful Drifter"
    ];
       
    const traitsOptions = ["Brave", "Cunning", "Resourceful", "Charismatic", "Loyal", "Independent"];
    const complications = ["Addiction","Betrayed","Code of Honor","Criminal Past","Daredevil","Dark Secret","Family Obligation","Famous","Loss","Outstanding Debt","Personal Enemy"];
    const motivations = ["Accumulate", "Build", "Find_Safety", "Hedonism", "Make_Amends", "Preach", "Protect", "Reunite"];

    character.concept = concepts[Math.floor(Math.random() * concepts.length)];
    character.traits = Array.from({ length: 3 }, () => traitsOptions[Math.floor(Math.random() * traitsOptions.length)]);

    // Initialize the RAPID Range attributes and Skills
    character.totals.attributes = { reason: 0, acumen: 0, physicality: 0, influence: 0, dexterity: 0 };
    character.totals.skills = {};

    // Distribute 5 points across RAPID Range attributes, max of 3 in any one attribute
    let pointsRemaining = 5;
    const attributes = Object.keys(character.totals.attributes);
    while (pointsRemaining > 0) {
        const randomAttribute = attributes[Math.floor(Math.random() * attributes.length)];
        if (character.totals.attributes[randomAttribute] < 3) {
            character.totals.attributes[randomAttribute]++;
            pointsRemaining--;
        }
    }

    // Distribute 15 points across Skills, max of 3 in any one skill
    pointsRemaining = 15;
    const skills = [
        "Animal_Handling (INF)", "Athletics (PHY)", "Barter (ACU)", "Demolitions* (PHY)", "Driving (DEX)", 
        "Farming (ACU)", "General_Knowledge (RSN)", "Inspiration (INF)", "Intimidation (INF)", "Manipulation (INF)", 
        "Mechanic* (RSN)", "Medicine* (RSN)", "Melee_Combat (PHY)", "Navigation (ACU)", "Psychology* (INF)", 
        "Ranged_Combat (DEX)", "Research (RSN)", "Scavenging (ACU)", "Sleight_of_Hand (DEX)", "Stealth (PHY)", 
        "Survival (ACU)", "Tactics* (RSN)", "Tinkerer (DEX)", "Unarmed_Combat (PHY)"
    ];
    while (pointsRemaining > 0) {
        const randomSkill = skills[Math.floor(Math.random() * skills.length)];
        if (!character.totals.skills[randomSkill]) {
            character.totals.skills[randomSkill] = 0;
        }
        if (character.totals.skills[randomSkill] < 3) {
            character.totals.skills[randomSkill]++;
            pointsRemaining--;
        }
    }

    // Randomly assign complication and motivation
    character.complicationsAndMotivations = {
        complication: complications[Math.floor(Math.random() * complications.length)],
        motivation: motivations[Math.floor(Math.random() * motivations.length)]
    };

    console.log("Random character generated:", character);
    showCharacterSummary();  // Directly show the character summary
}


// Helper function for handling the redistribution pool calculation based on excess points
function calculateRedistributionPool() {
    redistributionPool = 0;
    Object.entries(character.totals.attributes).forEach(([key, value]) => {
        if (value > 3) {
            redistributionPool += value - 3;
            character.totals.attributes[key] = 3;
        }
    });
    Object.entries(character.totals.skills).forEach(([key, value]) => {
        if (value > 3) {
            redistributionPool += value - 3;
            character.totals.skills[key] = 3;
        }
    });
}

// Helper function to calculate secondary stats based on attributes
function calculateSecondaryStats() {
    const { reason = 0, acumen = 0, physicality = 0, influence = 0, dexterity = 0 } = character.totals.attributes;
    return {
        woundPoints: 10 + physicality + dexterity,
        resiliencePoints: 6 + physicality,
        defensiveMelee: physicality,
        defensiveRange: dexterity,
        initiativeModifier: dexterity + acumen,
        encumbrance: 6 + physicality,
        perception: reason + acumen,
        morality: 3,
        panicThreshold: Math.floor((6 + physicality) / 2),
        breakingPoint: 0
    };
}

// Helper function to add points with a maximum cap of 3 and log each addition
function addPointsWithCap(obj, key, pointsToAdd, cap = 3) {
    const initialPoints = obj[key] || 0;
    const newValue = Math.min(initialPoints + pointsToAdd, cap);
    const addedPoints = newValue - initialPoints;

    obj[key] = newValue;
    redistributionPool += pointsToAdd - addedPoints; // Update redistribution pool for any excess points

    console.log(`addPointsWithCap - Key: ${key}, Initial: ${initialPoints}, Added: ${addedPoints}, New Value: ${obj[key]}, Redistribution Pool: ${redistributionPool}`);

    return pointsToAdd - addedPoints; // Return points to add to pool if over cap
}

// Helper to recalculate totals for accurate counts
function recalculateTotals() {
    const attributes = { reason: 0, acumen: 0, physicality: 0, influence: 0, dexterity: 0 };
    const skills = {};
    redistributionPool = 0; // Reset the redistribution pool

    // Step 1: Aggregate each step and cap values to ensure they do not exceed 3
    [character.childhood, character.education, character.hobbies, character.job, character.after].forEach(section => {
        if (section.attribute) {
            attributes[section.attribute] = Math.min(attributes[section.attribute] + 1, 3);
        }
        (section.skills || []).forEach(skill => {
            skills[skill] = Math.min((skills[skill] || 0) + 1, 3);
        });
    });

    // Step 2: Identify excess points and add them to the redistribution pool
    Object.entries(attributes).forEach(([key, value]) => {
        if (value > 3) {
            redistributionPool += value - 3;
            attributes[key] = 3; // Cap attribute to 3
        }
    });
    Object.entries(skills).forEach(([key, value]) => {
        if (value > 3) {
            redistributionPool += value - 3;
            skills[key] = 3; // Cap skill to 3
        }
    });

    // Step 3: Assign the capped values to character totals
    character.totals.attributes = attributes;
    character.totals.skills = skills;

    console.log("Totals recalculated:", character.totals, "Redistribution Pool:", redistributionPool);
}

// Helper Function to Update Totals with a cap of 3 for each attribute or skill
function updateTotals(attribute, skills) {
    if (attribute) {
        const cappedAttributeValue = Math.min((character.totals.attributes[attribute] || 0) + 1, 3);
        redistributionPool += character.totals.attributes[attribute] + 1 - cappedAttributeValue;
        character.totals.attributes[attribute] = cappedAttributeValue;
    }
    skills.forEach(skill => {
        const cappedSkillValue = Math.min((character.totals.skills[skill] || 0) + 1, 3);
        redistributionPool += (character.totals.skills[skill] || 0) + 1 - cappedSkillValue;
        character.totals.skills[skill] = cappedSkillValue;
    });
}


// Advance to the next step and log each transition
function nextStep() {
    console.log(`Entering nextStep: Current Step = ${step}`);

    if (step === 0) {
        showCharacterConceptStep();
    } else if (step === 1) {
        showChildhoodStep();
    } else if (step === 2) {
        showEducationStep();
    } else if (step === 3) {
        showHobbiesStep();
    } else if (step === 4) {
        showJobStep();
    } else if (step === 5) {
        showAfterStep();
    } else if (step === 6) {
        showComplicationsAndMotivationsStep();
    } else if (step === 7) {
        console.log("Final Step Reached: Displaying Character Summary");
        showCharacterSummary();
    } else {
        console.error("Unexpected step:", step);
        return;
    }

    step++;
    console.log(`Step incremented. New Step = ${step}`);
}


// Call showIntroPage on load to display the introduction page
showIntroPage();

// Step 0: Character Concept with formatted fields
function showCharacterConceptStep() {
    const container = document.getElementById('step-container');
    container.innerHTML = `
        <h2>Step 0: Character Concept</h2>
        <p>In this step you start to outline who your character is. 
        You should define their name, age, gender, and their profession.
        Define the basic concept of your character in a sentence or two. This should be something that grounds you and helps you with roleplaying.</br></br>
        Pick three descriptive words or traits that help define your character. </br></p>

        <div style="display: flex; flex-direction: column; gap: 10px;">
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="name">Character Name:</label>
                <input type="text" id="name" placeholder="Character Name">
            </div>
            
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="age">Age:</label>
                <input type="number" id="age" placeholder="Character Age" min="0">
            </div>
            
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="gender">Gender:</label>
                <input type="text" id="gender" placeholder="Character Gender">
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="profession">Profession:</label>
                <input type="text" id="profession" placeholder="Character Profession">
            </div>
            
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="concept">Character Concept:</label>
                <input type="text" id="concept" placeholder="Describe your character's core identity">
            </div>
            
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="traits">Three Descriptive Words (Comma-separated):</label>
                <input type="text" id="traits" placeholder="e.g., cautious, loyal, resourceful">
            </div>
        </div>
        
        <button onclick="saveCharacterConcept()" style="margin-top: 20px;">Next</button>
    `;
    console.log("Step 0: Character Concept page displayed.");
}

function saveCharacterConcept() {
    character.name = document.getElementById('name').value;
    character.age = document.getElementById('age').value;
    character.gender = document.getElementById('gender').value;
    character.profession = document.getElementById('profession').value;
    character.concept = document.getElementById('concept').value;
    character.traits = document.getElementById('traits').value.split(',').map(trait => trait.trim());

    console.log("Character concept saved:", character);
    nextStep();
}

// Step 1: Childhood
function showChildhoodStep() {
    const container = document.getElementById('step-container');
    container.innerHTML = `
        <h2>Step 1: Childhood</h2>
        <p>Where did your character grow up, and what shaped them during this phase of their life?</br></br>
        Select an attribute and skills that refect what your character learned during their childhood:</br>
        </p>

        <div style="display: flex; flex-direction: column; gap: 10px;">
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="childhood-attribute">Childhood RAPID Range:</label>
                <select id="childhood-attribute">
                    <option value="reason">Reason</option>
                    <option value="acumen">Acumen</option>
                    <option value="physicality">Physicality</option>
                    <option value="influence">Influence</option>
                    <option value="dexterity">Dexterity</option>
                </select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="childhood-skill1">Childhood Skill 1:</label>
                <select id="childhood-skill1">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="childhood-skill2">Childhood Skill 2:</label>
                <select id="childhood-skill2">${skillOptionsHTML}</select>
            </div>
        </div>
        
        <button onclick="saveChildhood()" style="margin-top: 20px;">Next</button>

        <!-- Character Summary Preview -->
        <div style="margin-top: 20px;">
            <b>${character.name || 'Character'} Preview</b></br>
            <b>Profession:</b> ${character.profession || 'N/A'}</br>
            <b>Concept:</b> ${character.concept || 'N/A'}</br>
            <b>Traits:</b> ${character.traits.join(', ') || 'N/A'}</br>
            <br>
            <!-- Small break before RAPID RANGE -->
            <br>

            <b>RAPID RANGE</b></br>
            <strong>Reason:</strong> ${character.totals.attributes.reason}</br>
            <strong>Acumen:</strong> ${character.totals.attributes.acumen}</br>
            <strong>Physicality:</strong> ${character.totals.attributes.physicality}</br>
            <strong>Influence:</strong> ${character.totals.attributes.influence}</br>
            <strong>Dexterity:</strong> ${character.totals.attributes.dexterity}</br>
        </div>
    `;
    console.log("Step 1: Childhood page displayed with character preview.");
}

function saveChildhood() {
    const attribute = document.getElementById('childhood-attribute').value;
    const skill1 = document.getElementById('childhood-skill1').value;
    const skill2 = document.getElementById('childhood-skill2').value;

    if (!attribute || !skill1 || !skill2) {
        alert("Please select an attribute and two skills before proceeding.");
        return;
    }

    character.childhood = { attribute, skills: [skill1, skill2] };
    redistributionPool += addPointsWithCap(character.totals.attributes, attribute, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill1, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill2, 1);

    console.log("Childhood data saved:", character.childhood);
    nextStep();
}

// Step 2: Education
function showEducationStep() {
    const container = document.getElementById('step-container');

    // Format skills to display each on a new line with attribute and value
    const skillAttributes = {
        animal_handling: 'INF',
        athletics: 'PHY',
        barter: 'ACU',
        demolitions: 'PHY',
        driving: 'DEX',
        farming: 'ACU',
        general_knowledge: 'RSN',
        inspiration: 'INF',
        intimidation: 'INF',
        manipulation: 'INF',
        mechanic: 'RSN',
        medicine: 'RSN',
        melee_combat: 'PHY',
        navigation: 'ACU',
        psychology: 'INF',
        ranged_combat: 'DEX',
        research: 'RSN',
        scavenging: 'ACU',
        sleight_of_hand: 'DEX',
        stealth: 'PHY',
        survival: 'ACU',
        tactics: 'RSN',
        tinkerer: 'DEX',
        unarmed_combat: 'PHY'
    };

    const formattedSkills = Object.entries(character.totals.skills)
        .map(([skill, value]) => {
            const attribute = skillAttributes[skill] || '';
            return `${skill.replace(/_/g, ' ')} ${attribute ? `(${attribute})` : ''} ${value}`;
        })
        .join('<br>');

    container.innerHTML = `
        <h2>Step 2: Education</h2>
        <p>Did your character have a formal education, or were they raised on the streets?</br></br>
        Select an attribute and skills related to your character’s education:</p>

        <div style="display: flex; flex-direction: column; gap: 10px;">
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="education-attribute">Education RAPID Range:</label>
                <select id="education-attribute">
                    <option value="reason">Reason</option>
                    <option value="acumen">Acumen</option>
                    <option value="physicality">Physicality</option>
                    <option value="influence">Influence</option>
                    <option value="dexterity">Dexterity</option>
                </select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="education-skill1">Education Skill 1:</label>
                <select id="education-skill1">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="education-skill2">Education Skill 2:</label>
                <select id="education-skill2">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="education-skill3">Education Skill 3:</label>
                <select id="education-skill3">${skillOptionsHTML}</select>
            </div>
        </div>
        
        <button onclick="saveEducation()" style="margin-top: 20px;">Next</button>

        <!-- Character Summary Preview -->
        <div style="margin-top: 20px;">
            <b>${character.name || 'Character'} Preview</b><br>
            <b>Profession:</b> ${character.profession || 'N/A'}<br>
            <b>Concept:</b> ${character.concept || 'N/A'}<br>
            <b>Traits:</b> ${character.traits.join(', ') || 'N/A'}<br>
            <br>

            <b>RAPID RANGE</b><br>
            <strong>Reason:</strong> ${character.totals.attributes.reason}<br>
            <strong>Acumen:</strong> ${character.totals.attributes.acumen}<br>
            <strong>Physicality:</strong> ${character.totals.attributes.physicality}<br>
            <strong>Influence:</strong> ${character.totals.attributes.influence}<br>
            <strong>Dexterity:</strong> ${character.totals.attributes.dexterity}<br>
            <br>

            <b>Skills:</b><br> ${formattedSkills || 'None'}
        </div>
    `;
    console.log("Step 2: Education page displayed with character preview.");
}

// `saveEducation()` with robust validation
function saveEducation() {
    const attribute = document.getElementById('education-attribute').value;
    const skill1 = document.getElementById('education-skill1').value;
    const skill2 = document.getElementById('education-skill2').value;
    const skill3 = document.getElementById('education-skill3').value;

    // Temporarily add points to check against max allowed values
    const testTotals = JSON.parse(JSON.stringify(character.totals));
    testTotals.attributes[attribute] = (testTotals.attributes[attribute] || 0) + 1;
    testTotals.skills[skill1] = (testTotals.skills[skill1] || 0) + 1;
    testTotals.skills[skill2] = (testTotals.skills[skill2] || 0) + 1;
    testTotals.skills[skill3] = (testTotals.skills[skill3] || 0) + 1;

    // Check if any attribute or skill exceeds 3
    const exceededAttributeLimit = Object.values(testTotals.attributes).some(value => value > 3);
    const exceededSkillLimit = Object.values(testTotals.skills).some(value => value > 3);

    if (exceededAttributeLimit || exceededSkillLimit) {
        alert("You cannot have more than 3 points in any attribute or skill. Please redistribute your points.");
        return; // Prevent moving to the next step
    }

    // Update character totals if validation passes
    character.education = { attribute, skills: [skill1, skill2, skill3] };
    redistributionPool += addPointsWithCap(character.totals.attributes, attribute, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill1, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill2, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill3, 1);

    console.log("Education data saved:", character.education);
    console.log("Redistribution Pool after Step 2:", redistributionPool); // Verify pool after update
    nextStep();  // Move to the next step only if validation passes
}

// Step 3: Hobbies
function showHobbiesStep() {
    const container = document.getElementById('step-container');

    // Define skill attributes
    const skillAttributes = {
        animal_handling: 'INF',
        athletics: 'PHY',
        barter: 'ACU',
        demolitions: 'PHY',
        driving: 'DEX',
        farming: 'ACU',
        general_knowledge: 'RSN',
        inspiration: 'INF',
        intimidation: 'INF',
        manipulation: 'INF',
        mechanic: 'RSN',
        medicine: 'RSN',
        melee_combat: 'PHY',
        navigation: 'ACU',
        psychology: 'INF',
        ranged_combat: 'DEX',
        research: 'RSN',
        scavenging: 'ACU',
        sleight_of_hand: 'DEX',
        stealth: 'PHY',
        survival: 'ACU',
        tactics: 'RSN',
        tinkerer: 'DEX',
        unarmed_combat: 'PHY'
    };

    // Format skills to match Step 2 format
    // Format and sort skills by level (descending) and name (alphabetical)
    const formattedSkills = Object.entries(character.totals.skills)
        .sort(([skillA, levelA], [skillB, levelB]) => {
            if (levelA === levelB) {
                return skillA.localeCompare(skillB);
            }
            return levelB - levelA; // Sort by level in descending order
    })
    .map(([skill, value]) => {
            const attribute = skillAttributes[skill] || '';
            return `${skill.replace(/_/g, ' ')} ${attribute ? `(${attribute})` : ''} ${value}`;
    })
    .join('<br>');

    container.innerHTML = `
        <h2>Step 3: Hobbies</h2>
        <p>Select an attribute and three skills for your character's hobbies.</p>

        <div style="display: flex; flex-direction: column; gap: 10px;">
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="hobbies-attribute">Hobbies RAPID Range:</label>
                <select id="hobbies-attribute">
                    <option value="reason">Reason</option>
                    <option value="acumen">Acumen</option>
                    <option value="physicality">Physicality</option>
                    <option value="influence">Influence</option>
                    <option value="dexterity">Dexterity</option>
                </select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="hobbies-skill1">Hobbies Skill 1:</label>
                <select id="hobbies-skill1">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="hobbies-skill2">Hobbies Skill 2:</label>
                <select id="hobbies-skill2">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="hobbies-skill3">Hobbies Skill 3:</label>
                <select id="hobbies-skill3">${skillOptionsHTML}</select>
            </div>
        </div>

        <button onclick="saveHobbies()" style="margin-top: 20px;">Next</button>

        <!-- Character Summary Preview -->
        <div style="margin-top: 20px;">
            <b>${character.name || 'Character'} Preview</b><br>
            <b>Profession:</b> ${character.profession || 'N/A'}<br>
            <b>Concept:</b> ${character.concept || 'N/A'}<br>
            <b>Traits:</b> ${character.traits.join(', ') || 'N/A'}<br>
            <br>

            <b>RAPID RANGE</b><br>
            <strong>Reason:</strong> ${character.totals.attributes.reason}<br>
            <strong>Acumen:</strong> ${character.totals.attributes.acumen}<br>
            <strong>Physicality:</strong> ${character.totals.attributes.physicality}<br>
            <strong>Influence:</strong> ${character.totals.attributes.influence}<br>
            <strong>Dexterity:</strong> ${character.totals.attributes.dexterity}<br>
            <br>

            <b>Skills:</b><br> ${formattedSkills || 'None'}
        </div>
    `;
    console.log("Step 3: Hobbies page displayed.");
}

// `saveHobbies()` with single-step increment
function saveHobbies() {
    const attribute = document.getElementById('hobbies-attribute').value;
    const skill1 = document.getElementById('hobbies-skill1').value;
    const skill2 = document.getElementById('hobbies-skill2').value;
    const skill3 = document.getElementById('hobbies-skill3').value;

    // Ensure all selections are made
    if (!attribute || !skill1 || !skill2 || !skill3) {
        alert("Please select an attribute and three skills for hobbies before proceeding.");
        return;
    }

    // Create a temporary totals object to test point addition without affecting actual totals
    const testTotals = JSON.parse(JSON.stringify(character.totals));
    testTotals.attributes[attribute] = (testTotals.attributes[attribute] || 0) + 1;
    testTotals.skills[skill1] = (testTotals.skills[skill1] || 0) + 1;
    testTotals.skills[skill2] = (testTotals.skills[skill2] || 0) + 1;
    testTotals.skills[skill3] = (testTotals.skills[skill3] || 0) + 1;

    // Check if any attribute or skill exceeds 3 points
    const exceededAttributeLimit = Object.values(testTotals.attributes).some(value => value > 3);
    const exceededSkillLimit = Object.values(testTotals.skills).some(value => value > 3);

    if (exceededAttributeLimit || exceededSkillLimit) {
        alert("You cannot have more than 3 points in any attribute or skill. Please redistribute your points.");
        return; // Prevent moving to the next step if limit is exceeded
    }

    // If validation passes, save the selections
    character.hobbies = { attribute, skills: [skill1, skill2, skill3] };
    redistributionPool += addPointsWithCap(character.totals.attributes, attribute, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill1, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill2, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill3, 1);

    console.log("Hobbies data saved:", character.hobbies);
    console.log("Redistribution Pool after Step 3:", redistributionPool);

    nextStep();  // Move to the next step only if validation passes
}


// Step 4: Job
function showJobStep() {
    console.log("Entered showJobStep() - Displaying Job selection page."); // Log this entry point
    const container = document.getElementById('step-container');

    // Define formattedSkills for displaying the skills preview
    const formattedSkills = Object.entries(character.totals.skills)
        .map(([skill, value]) => `${skill.replace(/_/g, ' ')} ${value}`)
        .join('<br>');

    container.innerHTML = `
        <h2>Step 4: Job</h2>
        <p>Select two attributes and four skills related to your character's job.</p>

        <div style="display: flex; flex-direction: column; gap: 10px;">
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="job-attribute1">Job RAPID Range 1:</label>
                <select id="job-attribute1">
                    <option value="reason">Reason</option>
                    <option value="acumen">Acumen</option>
                    <option value="physicality">Physicality</option>
                    <option value="influence">Influence</option>
                    <option value="dexterity">Dexterity</option>
                </select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="job-attribute2">Job RAPID Range 2:</label>
                <select id="job-attribute2">
                    <option value="reason">Reason</option>
                    <option value="acumen">Acumen</option>
                    <option value="physicality">Physicality</option>
                    <option value="influence">Influence</option>
                    <option value="dexterity">Dexterity</option>
                </select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="job-skill1">Job Skill 1:</label>
                <select id="job-skill1">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="job-skill2">Job Skill 2:</label>
                <select id="job-skill2">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="job-skill3">Job Skill 3:</label>
                <select id="job-skill3">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="job-skill4">Job Skill 4:</label>
                <select id="job-skill4">${skillOptionsHTML}</select>
            </div>
        </div>
        
        <button onclick="saveJob()" style="margin-top: 20px;">Next</button>

        <!-- Character Summary Preview -->
        <div style="margin-top: 20px;">
            <h3>${character.name || 'Character'} Preview</h3>
            <b>Profession:</b> ${character.profession || 'N/A'}<br>
            <b>Concept:</b> ${character.concept || 'N/A'}<br>
            <b>Traits:</b> ${character.traits.join(', ') || 'N/A'}<br>
            <br>
            <b>RAPID RANGE</b><br>
            <strong>Reason:</strong> ${character.totals.attributes.reason}<br>
            <strong>Acumen:</strong> ${character.totals.attributes.acumen}<br>
            <strong>Physicality:</strong> ${character.totals.attributes.physicality}<br>
            <strong>Influence:</strong> ${character.totals.attributes.influence}<br>
            <strong>Dexterity:</strong> ${character.totals.attributes.dexterity}<br>
            <br>
            <b>Skills:</b><br> ${formattedSkills || 'None'}
        </div>
    `;
    console.log("Step 4: Job page displayed with character preview.");
}

function saveJob() {
    console.log("Saving job data..."); // Start log
    const attribute1 = document.getElementById('job-attribute1').value;
    const attribute2 = document.getElementById('job-attribute2').value;
    const skill1 = document.getElementById('job-skill1').value;
    const skill2 = document.getElementById('job-skill2').value;
    const skill3 = document.getElementById('job-skill3').value;
    const skill4 = document.getElementById('job-skill4').value;

    // Temporarily add the points to totals to validate max points
    const testTotals = JSON.parse(JSON.stringify(character.totals));
    testTotals.attributes[attribute1] = (testTotals.attributes[attribute1] || 0) + 1;
    testTotals.attributes[attribute2] = (testTotals.attributes[attribute2] || 0) + 1;
    testTotals.skills[skill1] = (testTotals.skills[skill1] || 0) + 1;
    testTotals.skills[skill2] = (testTotals.skills[skill2] || 0) + 1;
    testTotals.skills[skill3] = (testTotals.skills[skill3] || 0) + 1;
    testTotals.skills[skill4] = (testTotals.skills[skill4] || 0) + 1;

    // Check if any attribute or skill exceeds 3
    const exceededAttributeLimit = Object.values(testTotals.attributes).some(value => value > 3);
    const exceededSkillLimit = Object.values(testTotals.skills).some(value => value > 3);

    if (exceededAttributeLimit || exceededSkillLimit) {
        alert("You cannot have more than 3 points in any attribute or skill. Please redistribute your points.");
        console.log("Job validation failed due to attribute/skill exceeding the limit."); // Add this log
        return; // Prevent moving to the next step
    }

    // If all values are valid, proceed to update character data
    character.job = { attributes: [attribute1, attribute2], skills: [skill1, skill2, skill3, skill4] };
    redistributionPool += addPointsWithCap(character.totals.attributes, attribute1, 1);
    redistributionPool += addPointsWithCap(character.totals.attributes, attribute2, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill1, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill2, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill3, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill4, 1);

    console.log("Job data saved successfully:", character.job);
    console.log("Redistribution Pool after Step 4:", redistributionPool); // Verify pool after update
    nextStep();  // Move to the next step
}

// Step 5: After
function showAfterStep() {
    const container = document.getElementById('step-container');
    
    // Ensure each section exists and is iterable by setting default empty arrays
    const childhoodSkills = character.childhood.skills || [];
    const educationSkills = character.education.skills || [];
    const hobbiesSkills = character.hobbies.skills || [];
    const jobSkills = character.job.skills || [];
    const afterSkills = character.after.skills || [];

    // Aggregate skills and count occurrences for cumulative summary preview
    const skillCounts = {};
    [...childhoodSkills, ...educationSkills, ...hobbiesSkills, ...jobSkills, ...afterSkills].forEach(skill => {
        skillCounts[skill] = (skillCounts[skill] || 0) + 1;
    });

    // Format skills to display each skill on a new line in "Skill count" format
    const formattedSkills = Object.entries(skillCounts)
        .map(([skill, count]) => `${skill.replace(/_/g, ' ')} ${count}`)
        .join('<br>');  // Display each skill on a new line

    container.innerHTML = `
        <h2>Step 5: After</h2>
        <p>The collapse of society was tough on everyone, and all survivors have picked up new skills and tricks to help them stay alive since.</br>
        </br>
        During this step, you can allocate 3 skill points based on what your character learned since the dog flu:</p>

        <div style="display: flex; flex-direction: column; gap: 10px;">
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="after-skill1">After Skill 1:</label>
                <select id="after-skill1">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="after-skill2">After Skill 2:</label>
                <select id="after-skill2">${skillOptionsHTML}</select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="after-skill3">After Skill 3:</label>
                <select id="after-skill3">${skillOptionsHTML}</select>
            </div>
        </div>
        
        <button onclick="saveAfter()" style="margin-top: 20px;">Next</button>

        <!-- Character Summary Preview -->
        <div style="margin-top: 20px;">
            <h3>${character.name || 'Character'} Preview</h3>
            <b>Profession:</b> ${character.profession || 'N/A'}<br>
            <b>Concept:</b> ${character.concept || 'N/A'}<br>
            <b>Traits:</b> ${character.traits.join(', ') || 'N/A'}<br>
            <br>
            <b>RAPID RANGE</b><br>
            <strong>Reason:</strong> ${character.totals.attributes.reason}<br>
            <strong>Acumen:</strong> ${character.totals.attributes.acumen}<br>
            <strong>Physicality:</strong> ${character.totals.attributes.physicality}<br>
            <strong>Influence:</strong> ${character.totals.attributes.influence}<br>
            <strong>Dexterity:</strong> ${character.totals.attributes.dexterity}<br>
            <br>
            <b>Skills:</b><br> ${formattedSkills || 'None'}
        </div>
    `;
    console.log("Step 5: After page displayed with character preview.");
}

function saveAfter() {
    const skill1 = document.getElementById('after-skill1').value;
    const skill2 = document.getElementById('after-skill2').value;
    const skill3 = document.getElementById('after-skill3').value;

    if (!skill1 || !skill2 || !skill3) {
        alert("Please select three skills for 'After' before proceeding.");
        return;
    }

    character.after = { skills: [skill1, skill2, skill3] };
    redistributionPool += addPointsWithCap(character.totals.skills, skill1, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill2, 1);
    redistributionPool += addPointsWithCap(character.totals.skills, skill3, 1);

    console.log("After data saved:", character.after);
    console.log("Redistribution Pool after Step 5:", redistributionPool);

    // Log before advancing to next step
    console.log("Advancing from Step 5 to Step 6...");
    nextStep();  // Move to the next step only once
}

// Step 6: Complications and Motivaitons 
function showComplicationsAndMotivationsStep() {
    // Define skill attributes and build formattedSkills for this step
    const skillAttributes = {
        animal_handling: 'INF',
        athletics: 'PHY',
        barter: 'ACU',
        demolitions: 'PHY',
        driving: 'DEX',
        farming: 'ACU',
        general_knowledge: 'RSN',
        inspiration: 'INF',
        intimidation: 'INF',
        manipulation: 'INF',
        mechanic: 'RSN',
        medicine: 'RSN',
        melee_combat: 'PHY',
        navigation: 'ACU',
        psychology: 'INF',
        ranged_combat: 'DEX',
        research: 'RSN',
        scavenging: 'ACU',
        sleight_of_hand: 'DEX',
        stealth: 'PHY',
        survival: 'ACU',
        tactics: 'RSN',
        tinkerer: 'DEX',
        unarmed_combat: 'PHY'
    };

    // Format skills for display in the character summary
    const formattedSkills = Object.entries(character.totals.skills)
        .filter(([skill, value]) => value > 0)
        .sort((a, b) => b[1] - a[1] || a[0].localeCompare(b[0]))
        .map(([skill, value]) => `${capitalizeWords(skill)}${skillAttributes[skill] ? ` (${skillAttributes[skill]})` : ''} ${value}`)
        .join('<br>');

    // Display Complications and Motivations Step with dropdowns
    const container = document.getElementById('step-container');
    container.innerHTML = `
        <h2>Step 6: Complications & Motivations</h2>
        <p>Select a complication and a motivation to define what drives your character and what challenges them:</p>
        
        <div style="display: flex; flex-direction: column; gap: 10px;">
            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="complication">Complication:</label>
                <select id="complication">
                    <option value="Addiction">Addiction</option>
                    <option value="Betrayed">Betrayed</option>
                    <option value="Code of Honor">Code of Honor</option>
                    <option value="Criminal Past">Criminal Past</option>
                    <option value="Daredevil">Daredevil</option>
                    <option value="Dark Secret">Dark Secret</option>
                    <option value="Family Obligation">Family Obligation</option>
                    <option value="Famous">Famous</option>
                    <option value="Loss">Loss</option>
                    <option value="Outstanding Debt">Outstanding Debt</option>
                    <option value="Personal Enemy">Personal Enemy</option>
                </select>
            </div>

            <div style="display: flex; align-items: center; gap: 10px;">
                <label for="motivation">Motivation:</label>
                <select id="motivation">
                    <option value="Accumulate">Accumulate</option>
                    <option value="Build">Build</option>
                    <option value="Find Safety">Find Safety</option>
                    <option value="Hedonism">Hedonism</option>
                    <option value="Make Amends">Make Amends</option>
                    <option value="Preach">Preach</option>
                    <option value="Protect">Protect</option>
                    <option value="Reunite">Reunite</option>
                    <option value="Revenge">Revenge</option>
                    <option value="Stay Alive">Stay Alive</option>
                    <option value="Take Advantage">Take Advantage</option>
                </select>
            </div>
        </div>

        <button onclick="saveComplicationsAndMotivations()" style="margin-top: 20px;">Next</button>

        <!-- Character Summary Preview -->
        <div style="margin-top: 20px;">
            <h3>${character.name || 'Character'} Preview</h3>
            <b>Profession:</b> ${character.profession || 'N/A'}<br>
            <b>Concept:</b> ${character.concept || 'N/A'}<br>
            <b>Traits:</b> ${character.traits.join(', ') || 'N/A'}<br>
            <br>
            <b>RAPID RANGE</b><br>
            <strong>Reason:</strong> ${character.totals.attributes.reason}<br>
            <strong>Acumen:</strong> ${character.totals.attributes.acumen}<br>
            <strong>Physicality:</strong> ${character.totals.attributes.physicality}<br>
            <strong>Influence:</strong> ${character.totals.attributes.influence}<br>
            <strong>Dexterity:</strong> ${character.totals.attributes.dexterity}<br>
            <br>
            <b>Skills:</b><br> ${formattedSkills || 'None'}
        </div>
    `;
    console.log("Step 6: Complications and Motivations summary displayed.");
}

function saveComplicationsAndMotivations() {
    const complication = document.getElementById('complication').value;
    const motivation = document.getElementById('motivation').value;

    if (!complication || !motivation) {
        alert("Please select both a complication and a motivation before proceeding.");
        return; // Stop if selections are missing
    }

    // Save complication and motivation to character object
    character.complicationsAndMotivations = { complication, motivation };

    console.log("Complications and Motivations saved:", character.complicationsAndMotivations);

    // Move to the next step after saving
    nextStep();
}


// redistribuion 
function saveRedistribution() {
    const totalExcessCDP = document.querySelectorAll('[id^="redistribute-skill-"]').length;

    // Redistribute points as per user selections
    for (let i = 0; i < totalExcessCDP; i++) {
        const selectedSkill = document.getElementById(`redistribute-skill-${i + 1}`).value;
        character.totals.skills[selectedSkill] = Math.min((character.totals.skills[selectedSkill] || 0) + 1, 3);
    }

    console.log("Redistributed CDP values saved:", character.totals);

    // Generate summary immediately after redistribution is complete
    showCharacterSummary();
}

// Helper function to capitalize each word in a string
function capitalizeWords(str) {
    return str.replace(/\b\w/g, char => char.toUpperCase());
}

// Step 8: Character Summary and Download
function showCharacterSummary() {
    const container = document.getElementById('step-container');

    // Base attribute mappings for each skill
    const skillAttributes = {
        animal_handling: 'INF', athletics: 'PHY', barter: 'ACU', demolitions: 'PHY', driving: 'DEX',
        farming: 'ACU', general_knowledge: 'RSN', inspiration: 'INF', intimidation: 'INF', manipulation: 'INF',
        mechanic: 'RSN', medicine: 'RSN', melee_combat: 'PHY', navigation: 'ACU', psychology: 'INF',
        ranged_combat: 'DEX', research: 'RSN', scavenging: 'ACU', sleight_of_hand: 'DEX', stealth: 'PHY',
        survival: 'ACU', tactics: 'RSN', tinkerer: 'DEX', unarmed_combat: 'PHY'
    };

    // Helper to capitalize each word in a skill name
    const capitalizeWords = (str) => str.replace(/_/g, ' ').replace(/\b\w/g, char => char.toUpperCase());

    // Format skills: only non-zero values, sorted by value (desc), then alphabetically
    const formattedSkills = Object.entries(character.totals.skills)
        .filter(([_, value]) => value > 0)
        .sort((a, b) => b[1] - a[1] || a[0].localeCompare(b[0]))
        .map(([skill, value]) => `${capitalizeWords(skill)}${skillAttributes[skill] ? ` (${skillAttributes[skill]})` : ''} ${value}`)
        .join('<br>');

    // Display character summary
    container.innerHTML = `
        <h2>${character.name || 'Character'} Summary</h2>

        <h3>1. Basic Info</h3>
        <div>
            <strong>Name:</strong> ${character.name || 'N/A'}<br>
            <strong>Age:</strong> ${character.age || 'N/A'}<br>
            <strong>Gender:</strong> ${character.gender || 'N/A'}<br>
            <strong>Profession:</strong> ${character.profession || 'N/A'}<br>
            <strong>Concept:</strong> ${character.concept || 'N/A'}<br>
            <strong>Traits:</strong> ${character.traits.join(', ') || 'N/A'}<br>
            <strong>Complication:</strong> ${capitalizeWords(character.complicationsAndMotivations.complication || 'N/A')}<br>
            <strong>Motivation:</strong> ${capitalizeWords(character.complicationsAndMotivations.motivation || 'N/A')}

        </div>

        <h3>2. RAPID Range Attributes</h3>
        <div>
            <strong>Reason:</strong> ${character.totals.attributes.reason}<br>
            <strong>Acumen:</strong> ${character.totals.attributes.acumen}<br>
            <strong>Physicality:</strong> ${character.totals.attributes.physicality}<br>
            <strong>Influence:</strong> ${character.totals.attributes.influence}<br>
            <strong>Dexterity:</strong> ${character.totals.attributes.dexterity}
        </div>

        <h3>3. Skills</h3>
        <div style="white-space: pre;"><b>Skills:</b><br>${formattedSkills || 'None'}</div>

        <button onclick="downloadCharacter()" style="margin-top: 20px;">Download Character Sheet</button>
    `;

    console.log("Character summary displayed:", character);
}

// Function to download the character summary
function downloadCharacter() {
    const skillAttributes = {
        animal_handling: 'INF', athletics: 'PHY', barter: 'ACU', demolitions: 'PHY', driving: 'DEX',
        farming: 'ACU', general_knowledge: 'RSN', inspiration: 'INF', intimidation: 'INF', manipulation: 'INF',
        mechanic: 'RSN', medicine: 'RSN', melee_combat: 'PHY', navigation: 'ACU', psychology: 'INF',
        ranged_combat: 'DEX', research: 'RSN', scavenging: 'ACU', sleight_of_hand: 'DEX', stealth: 'PHY',
        survival: 'ACU', tactics: 'RSN', tinkerer: 'DEX', unarmed_combat: 'PHY'
    };
    
    const characterData = `
Name: ${character.name || 'N/A'}
Age: ${character.age || 'N/A'}
Gender: ${character.gender || 'N/A'}
Profession: ${character.profession || 'N/A'}
Concept: ${character.concept || 'N/A'}
Traits: ${character.traits.join(', ') || 'N/A'}
Complication: ${capitalizeWords(character.complicationsAndMotivations.complication || 'N/A')}
Motivation: ${capitalizeWords(character.complicationsAndMotivations.motivation || 'N/A')}

RAPID Range Attributes:
Reason: ${character.totals.attributes.reason}
Acumen: ${character.totals.attributes.acumen}
Physicality: ${character.totals.attributes.physicality}
Influence: ${character.totals.attributes.influence}
Dexterity: ${character.totals.attributes.dexterity}

Skills:
${Object.entries(character.totals.skills)
        .filter(([_, value]) => value > 0)
        .map(([skill, value]) => `${capitalizeWords(skill)} (${skillAttributes[skill] || ''}) ${value}`)
        .join('\n')}
`;

    // Create a Blob from the character data
    const blob = new Blob([characterData], { type: 'text/plain' });
    const url = URL.createObjectURL(blob);

    // Create a link to download the file
    const link = document.createElement('a');
    link.href = url;
    link.download = `${character.name || 'Character'}_Sheet.txt`;
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
    URL.revokeObjectURL(url);

    console.log("Character sheet downloaded.");
}
