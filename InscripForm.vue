<template>
    <section class="form-container">
      <form id="msform" @submit.prevent="submitForm">
        <ul id="progressbar">
          <li :class="{ active: step === 1 }">Identifiants du compte</li>
          <li :class="{ active: step === 2 }">Coordonnées Représentant</li>
          <li :class="{ active: step === 3 }">Informations Entreprise</li>
        </ul>
  
        <fieldset v-if="step === 1">
  <h2 class="fs-title">Identifiants du compte</h2>
  <input type="email" v-model="email" required placeholder="Email@domaine" />
  <div class="password-container">
    <input :type="showPassword ? 'text' : 'password'" v-model="password" required placeholder="Mot de passe" />
    <span class="eye-pass" @click="togglePassword">👁️</span>
  </div>
  <div class="password-container">
    <input :type="showPassword ? 'text' : 'password'" v-model="password2" required placeholder="Confirmation mot de passe" />
    <span class="eye-pass" @click="togglePassword">👁️</span>
  </div>
  <button type="button" @click="nextStep">Suivant</button>
        </fieldset>
  
        <fieldset v-if="step === 2">
          <h2 class="fs-title">Coordonnées Représentant</h2>
          <input type="text" v-model="nomEntreprise" required placeholder="Nom de l'entreprise" />
          <select v-model="civilite" required>
            <option value="Monsieur">Monsieur</option>
            <option value="Madame">Madame</option>
          </select>
          <input type="text" v-model="nomRepresentant" required placeholder="Nom du représentant" />
          <input type="text" v-model="prenomRepresentant" required placeholder="Prénom" />
          <input type="text" v-model="fonction" required placeholder="Fonction" />
          <input type="text" v-model="numero" required placeholder="Numéro de téléphone" />
          <select id="pays" name="pays" required="required"   onchange="executeme(this.value)">
            <option value="0">--Pays--</option>
            <option value="1" > Afghanistan</option>
						    									<option value="2" > Afrique du Sud</option>
						    									<option value="3" > Albanie</option>
						    									<option value="4" > Algérie</option>
						    									<option value="5" > Allemagne</option>
						    									<option value="6" > Andorre</option>
						    									<option value="7" > Angola</option>
						    									<option value="8" > Anguilla</option>
						    									<option value="9" > Antigua-et-Barbuda</option>
						    									<option value="10" > Antilles Néerlandaises</option>
						    									<option value="11" > Arabie Saoudite</option>
						    									<option value="12" > Argentine</option>
						    									<option value="13" > Arménie</option>
						    									<option value="14" > Aruba</option>
						    									<option value="15" > Australie</option>
						    									<option value="16" > Autriche</option>
						    									<option value="17" > Azerbaïdjan</option>
						    									<option value="18" > Bahamas</option>
						    									<option value="19" > Bahreïn</option>
						    									<option value="20" > Bangladesh</option>
						    									<option value="21" > Barbade</option>
						    									<option value="22" > Belgique</option>
						    									<option value="23" > Belize</option>
						    									<option value="24" > Bénin</option>
						    									<option value="25" > Bermudes</option>
						    									<option value="26" > Bhoutan</option>
						    									<option value="27" > Biélorussie</option>
						    									<option value="28" > Birmanie (Myanmar)</option>
						    									<option value="29" > Bolivie</option>
						    									<option value="30" > Bosnie-Herzégovine</option>
						    									<option value="31" > Botswana</option>
						    									<option value="32" > Brésil</option>
						    									<option value="33" > Brunei</option>
						    									<option value="34" > Bulgarie</option>
						    									<option value="35" > Burkina Faso</option>
						    									<option value="36" > Burundi</option>
						    									<option value="37" > Cambodge</option>
						    									<option value="38" > Cameroun</option>
						    									<option value="39" > Canada</option>
						    									<option value="40" > Cap-vert</option>
						    									<option value="41" > Chili</option>
						    									<option value="42" > Chine</option>
						    									<option value="43" > Chypre</option>
						    									<option value="44" > Colombie</option>
						    									<option value="45" > Comores</option>
						    									<option value="46" > Corée du Nord</option>
						    									<option value="47" > Corée du Sud</option>
						    									<option value="48" > Costa Rica</option>
						    									<option value="49" > Côte d'Ivoire</option>
						    									<option value="50" > Croatie</option>
						    									<option value="51" > Cuba</option>
						    									<option value="52" > Danemark</option>
						    									<option value="53" > Djibouti</option>
						    									<option value="54" > Dominique</option>
						    									<option value="55" > Égypte</option>
						    									<option value="56" > Émirats Arabes Unis</option>
						    									<option value="57" > Équateur</option>
						    									<option value="58" > Érythrée</option>
						    									<option value="59" > Espagne</option>
						    									<option value="60" > Estonie</option>
						    									<option value="61" > États Fédérés de Micronésie</option>
						    									<option value="62" > États-Unis</option>
						    									<option value="63" > Éthiopie</option>
						    									<option value="64" > Fidji</option>
						    									<option value="65" > Finlande</option>
						    									<option value="66" > France</option>
						    									<option value="67" > Gabon</option>
						    									<option value="68" > Gambie</option>
						    									<option value="69" > Géorgie</option>
						    									<option value="70" > Géorgie du Sud et les Îles Sandwich du Sud</option>
						    									<option value="71" > Ghana</option>
						    									<option value="72" > Gibraltar</option>
						    									<option value="73" > Grèce</option>
						    									<option value="74" > Grenade</option>
						    									<option value="75" > Groenland</option>
						    									<option value="76" > Guadeloupe</option>
						    									<option value="77" > Guam</option>
						    									<option value="78" > Guatemala</option>
						    									<option value="79" > Guinée</option>
						    									<option value="80" > Guinée-Bissau</option>
						    									<option value="81" > Guinée Équatoriale</option>
						    									<option value="82" > Guyana</option>
						    									<option value="83" > Guyane Française</option>
						    									<option value="84" > Haïti</option>
						    									<option value="85" > Honduras</option>
						    									<option value="86" > Hong-Kong</option>
						    									<option value="87" > Hongrie</option>
						    									<option value="88" > Île Christmas</option>
						    									<option value="89" > Île de Man</option>
						    									<option value="90" > Île Norfolk</option>
						    									<option value="91" > Îles Åland</option>
						    									<option value="92" > Îles Caïmanes</option>
						    									<option value="93" > Îles Cocos (Keeling)</option>
						    									<option value="94" > Îles Cook</option>
						    									<option value="95" > Îles Féroé</option>
						    									<option value="96" > Îles Malouines</option>
						    									<option value="97" > Îles Mariannes du Nord</option>
						    									<option value="98" > Îles Marshall</option>
						    									<option value="99" > Îles Pitcairn</option>
						    									<option value="100" > Îles Salomon</option>
						    									<option value="101" > Îles Turks et Caïques</option>
						    									<option value="102" > Îles Vierges Britanniques</option>
						    									<option value="103" > Îles Vierges des États-Unis</option>
						    									<option value="104" > Inde</option>
						    									<option value="105" > Indonésie</option>
						    									<option value="106" > Iran</option>
						    									<option value="107" > Iraq</option>
						    									<option value="108" > Irlande</option>
						    									<option value="109" > Islande</option>
						    									<option value="110" > Italie</option>
						    									<option value="111" > Jamaïque</option>
						    									<option value="112" > Japon</option>
						    									<option value="113" > Jordanie</option>
						    									<option value="114" > Kazakhstan</option>
						    									<option value="115" > Kenya</option>
						    									<option value="116" > Kirghizistan</option>
						    									<option value="117" > Kiribati</option>
						    									<option value="118" > Koweït</option>
						    									<option value="119" > Laos</option>
						    									<option value="120" > Le Vatican</option>
						    									<option value="121" > Lesotho</option>
						    									<option value="122" > Lettonie</option>
						    									<option value="123" > Liban</option>
						    									<option value="124" > Libéria</option>
						    									<option value="125" > Libye</option>
						    									<option value="126" > Liechtenstein</option>
						    									<option value="127" > Lituanie</option>
						    									<option value="128" > Luxembourg</option>
						    									<option value="129" > Macao</option>
						    									<option value="130" > Madagascar</option>
						    									<option value="131" > Malaisie</option>
						    									<option value="132" > Malawi</option>
						    									<option value="133" > Maldives</option>
						    									<option value="134" > Mali</option>
						    									<option value="135" > Malte</option>
						    									<option value="136" > Maroc</option>
						    									<option value="137" > Martinique</option>
						    									<option value="138" > Maurice</option>
						    									<option value="139" > Mauritanie</option>
						    									<option value="140" > Mayotte</option>
						    									<option value="141" > Mexique</option>
						    									<option value="142" > Moldavie</option>
						    									<option value="143" > Monaco</option>
						    									<option value="144" > Mongolie</option>
						    									<option value="145" > Monténégro</option>
						    									<option value="146" > Montserrat</option>
						    									<option value="147" > Mozambique</option>
						    									<option value="148" > Namibie</option>
						    									<option value="149" > Nauru</option>
						    									<option value="150" > Népal</option>
						    									<option value="151" > Nicaragua</option>
						    									<option value="152" > Niger</option>
						    									<option value="153" > Nigéria</option>
						    									<option value="154" > Niué</option>
						    									<option value="155" > Norvège</option>
						    									<option value="156" > Nouvelle-Calédonie</option>
						    									<option value="157" > Nouvelle-Zélande</option>
						    									<option value="158" > Oman</option>
						    									<option value="159" > Ouganda</option>
						    									<option value="160" > Ouzbékistan</option>
						    									<option value="161" > Pakistan</option>
						    									<option value="162" > Palaos</option>
						    									<option value="163" > Palestine</option>
						    									<option value="164" > Panama</option>
						    									<option value="165" > Papouasie-Nouvelle-Guinée</option>
						    									<option value="166" > Paraguay</option>
						    									<option value="167" > Pays-Bas</option>
						    									<option value="168" > Pérou</option>
						    									<option value="169" > Philippines</option>
						    									<option value="170" > Pologne</option>
						    									<option value="171" > Polynésie Française</option>
						    									<option value="172" > Porto Rico</option>
						    									<option value="173" > Portugal</option>
						    									<option value="174" > Qatar</option>
						    									<option value="175" > République Centrafricaine</option>
						    									<option value="176" > République de Macédoine</option>
						    									<option value="177" > République Démocratique du Congo</option>
						    									<option value="178" > République Dominicaine</option>
						    									<option value="179" > République du Congo</option>
						    									<option value="180" > République Tchèque</option>
						    									<option value="181" > Réunion</option>
						    									<option value="182" > Roumanie</option>
						    									<option value="183" > Royaume-Uni</option>
						    									<option value="184" > Russie</option>
						    									<option value="185" > Rwanda</option>
						    									<option value="186" > Sahara Occidental</option>
						    									<option value="187" > Saint-Kitts-et-Nevis</option>
						    									<option value="188" > Saint-Marin</option>
						    									<option value="189" > Saint-Pierre-et-Miquelon</option>
						    									<option value="190" > Saint-Vincent-et-les Grenadines</option>
						    									<option value="191" > Sainte-Hélène</option>
						    									<option value="192" > Sainte-Lucie</option>
						    									<option value="193" > Salvador</option>
						    									<option value="194" > Samoa</option>
						    									<option value="195" > Samoa Américaines</option>
						    									<option value="196" > Sao Tomé-et-Principe</option>
						    									<option value="197" > Sénégal</option>
						    									<option value="198" > Serbie</option>
						    									<option value="199" > Seychelles</option>
						    									<option value="200" > Sierra Leone</option>
						    									<option value="201" > Singapour</option>
						    									<option value="202" > Slovaquie</option>
						    									<option value="203" > Slovénie</option>
						    									<option value="204" > Somalie</option>
						    									<option value="205" > Soudan</option>
						    									<option value="206" > Sri Lanka</option>
						    									<option value="207" > Suède</option>
						    									<option value="208" > Suisse</option>
						    									<option value="209" > Suriname</option>
						    									<option value="210" > Svalbard et Jan Mayen</option>
						    									<option value="211" > Swaziland</option>
						    									<option value="212" > Syrie</option>
						    									<option value="213" > Tadjikistan</option>
						    									<option value="214" > Taïwan</option>
						    									<option value="215" > Tanzanie</option>
						    									<option value="216" > Tchad</option>
						    									<option value="217" > Terres Australes Françaises</option>
						    									<option value="218" > Thaïlande</option>
						    									<option value="219" > Timor Oriental</option>
						    									<option value="220" > Togo</option>
						    									<option value="221" > Tonga</option>
						    									<option value="222" > Trinité-et-Tobago</option>
						    									<option value="223" > Tunisie</option>
						    									<option value="224" > Turkménistan</option>
						    									<option value="225" > Turquie</option>
						    									<option value="226" > Tuvalu</option>
						    									<option value="227" > Ukraine</option>
						    									<option value="228" > Uruguay</option>
						    									<option value="229" > Vanuatu</option>
						    									<option value="230" > Venezuela</option>
						    									<option value="231" > Viet Nam</option>
						    									<option value="232" > Wallis et Futuna</option>
						    									<option value="233" > Yémen</option>
						    									<option value="234" > Zambie</option>
						    									<option value="235" > Zimbabwe</option>
          </select>

          <select name="wilaya" required="required" id="wilaya">
							<option value='0'>--Wilaya--</option>
						</select>
					
         
          <input type="text" v-model="adresse" required placeholder="Adresse" />
          <button type="button" @click="prevStep">Précédent</button>
          <button type="button" @click="nextStep">Suivant</button>
        </fieldset>
  
        <fieldset v-if="step === 3">
          <h2 class="fs-title">Informations Entreprise</h2>
          <select name="activite" required="required">

          <option value="0">--Activité--</option>
																			<option value="Aéronautique" > Aéronautique</option>
						
								  												<option value="Agriculture" > Agriculture</option>
						
								  												<option value="Elevage" > Elevage</option>
						
								  												<option value="Forêts et Pêche" > Forêts et Pêche</option>
						
								  												<option value="Agro alimentaire" > Agro alimentaire</option>
						
								  												<option value="Ameublement et Mobilier" > Ameublement et Mobilier</option>
						
								  												<option value="Architecture et Urbanisme" > Architecture et Urbanisme</option>
						
								  												<option value="Assurance et Banque" > Assurance et Banque</option>
						
								  												<option value="Bâtiment et Génie civil" > Bâtiment et Génie civil</option>
						
								  												<option value="Chimie" > Chimie</option>
						
								  												<option value="Pétrochimie" > Pétrochimie</option>
						
								  												<option value="Energie et Service pétrolier" > Energie et Service pétrolier</option>
						
								  												<option value="Equipement industriel" > Equipement industriel</option>
						
								  												<option value="Outillage et Pièce détachée" > Outillage et Pièce détachée</option>
						
								  												<option value="Restauration" > Restauration</option>
						
								  												<option value="Hôtellerie " > Hôtellerie </option>
						
								  												<option value="Equipement pour les collectivités et villes" > Equipement pour les collectivités et villes</option>
						
								  												<option value="Etudes" > Etudes</option>
						
								  												<option value="Consulting" > Consulting</option>
						
								  												<option value="Formation et Certification" > Formation et Certification</option>
						
								  												<option value="Hydraulique et Environnement" > Hydraulique et Environnement</option>
						
								  												<option value="Immobilier" > Immobilier</option>
						
								  												<option value="Impression" > Impression</option>
						
								  												<option value="Edition et Communication" > Edition et Communication</option>
						
								  												<option value="Industrie de la cellulose" > Industrie de la cellulose</option>
						
								  												<option value="Papier" > Papier</option>
						
								  												<option value="Carton et Emballage" > Carton et Emballage</option>
						
								  												<option value="Industrie électrique et Electrotechnique" > Industrie électrique et Electrotechnique</option>
						
								  												<option value="Industrie manufacturière" > Industrie manufacturière</option>
						
								  												<option value="Industrie sidérurgique" > Industrie sidérurgique</option>
						
								  												<option value="Métallurgique et Mécanique" > Métallurgique et Mécanique</option>
						
								  												<option value="Informatique et Bureautique" > Informatique et Bureautique</option>
						
								  												<option value="Médical et Paramédical" > Médical et Paramédical</option>
						
								  												<option value="Mine" > Mine</option>
						
								  												<option value="Cimenterie" > Cimenterie</option>
						
								  												<option value="Agrégat et Granulat" > Agrégat et Granulat</option>
						
								  												<option value="Pharmacie et Parapharmacie" > Pharmacie et Parapharmacie</option>
						
								  												<option value="Port et Aéroport" > Port et Aéroport</option>
						
								  												<option value="Sécurité et HSE" > Sécurité et HSE</option>
						
								  												<option value="Service" > Service</option>
						
								  												<option value="Sport et Loisirs" > Sport et Loisirs</option>
						
								  												<option value="Equipement scientifique et Laboratoire" > Equipement scientifique et Laboratoire</option>
						
								  												<option value="Télécommunication" > Télécommunication</option>
						
								  												<option value="Transport" > Transport</option>
						
								  												<option value="Travaux publics" > Travaux publics</option>
						
								  												<option value="Industrie électronique et Matériel audio-visuel" > Industrie électronique et Matériel audio-visuel</option>
						

    								  												<option value="Autre" > Autre</option>
          </select>
						<select name="categorie" required="required" onchange="changeCategorie(this.value)">
								<option value="0">--Catégorie de l'entreprise--</option>
								<option value="ANGEM" >ANGEM</option>
								<option value="CNAC" >CNAC</option>
								<option value="ANSEJ" >ANSEJ</option>
								<option value="TPE (STARTUP)" >TPE (STARTUP)</option>
								<option value="PME/PMI" >PME/PMI</option>
								<option value="SARL" >SARL</option>
								<option value="EURL" >EURL</option>
								<option value="EPIC" >EPIC</option>
								<option value="SCS" >SCS</option>
								<option value="Entreprise Publique" >Entreprise Publique</option>
								<option value="SPA" >SPA</option>
								<option value="SNC" >SNC</option>
								<option value="Personne Physique" >Personne Physique</option>
						</select>
          <input type="text" v-model="codeCommerce" required placeholder="Code Commerce" />
          <input type="text" v-model="nif" required placeholder="NIF" />
          <input type="text" v-model="nis" required placeholder="NIS" />
          <input type="text" v-model="nin" required placeholder="NIN" />
          <select name="nbr_employe" required="required">
								<option value="0">--Nombre d'employé--</option>
								<option value="-10" >moins de 10</option>
								<option value="10-49" >de 10 à 49</option>
								<option value="50-249" >de 50 à 249</option>
								<option value="+250" >plus de 250</option>
						</select>
   
          <button type="button" @click="prevStep">Précédent</button>
 <div id="recaptcha-container" class="recaptcha-box">
          <div class="g-recaptcha" data-sitekey="6LdGRdMqAAAAACAf9oAZuVn0LRSrs2LCTSztT5hc"></div>
        </div>
    <Recaptcha @verified="handleCaptchaVerified" />
    <button type="submit">S'inscrire</button>
  
        </fieldset>
      </form>
    </section>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
	name: 'InscripForm',
	data() {
	  return {
		step: 1,
		email: '',
		password: '',
		password2: '',
		showPassword: false,
		nomEntreprise: '',
		civilite: '',
		nomRepresentant: '',
		prenomRepresentant: '',
		fonction: '',
		numero: '',
		selectedCountry: '',
		selectedWilaya: '',
		wilayas: [],
		wilayaRequired: false,
		adresse: '',
		codeCommerce: '',
		nif: '',
		nis: '',
		nin: '',
		captchaResponse: '', 
		captchaSrc: '',     
		captchaResponse: null
 
	  };
	},
	methods: {
	  togglePassword() {
		this.showPassword = !this.showPassword;
	  },
	  nextStep() {
		if (this.step < 3) this.step++;
	  },
	  prevStep() {
		if (this.step > 1) this.step--;
	  },
	  async fetchWilayas() {
		try {
		  const response = await axios.post('https://www.safqatic.dz/api_getregion.php', { id: this.selectedCountry });
		  this.wilayas = response.data;
		} catch (error) {
		  console.error('Erreur de récupération des wilayas:', error);
		}
	  },
	  updateWilayaRequirement() {
		this.wilayaRequired = this.selectedCountry === '4';
		this.fetchWilayas();
	  },
	  refreshCaptcha() {
		this.captchaSrc = "captcha/captcha.php?" + Math.random();
	  },
	  handleCaptchaVerified(response) {
		this.captchaResponse = response;
	  },
	  submitForm() {
		if (!this.captchaResponse) {
		  alert('Veuillez compléter le captcha avant de soumettre le formulaire.');
		  return;
		}
	  },
	  onVerify(token) {
		this.$emit('verified', token);
	  },
	},
	mounted() {
    if (!window.grecaptcha) {
      console.error('Le script reCAPTCHA n\'est pas chargé. Assurez-vous d\'avoir ajouté la balise');
    }
  }
};

  </script>
  
    
  <style scoped>
.form-container {
  width: 40%;
  margin: 50px auto;
  position: relative;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 0 15px 1px rgba(0, 0, 0, 0.4);
  padding: 30px;
}

#msform {
  text-align: center;
  position: relative;
}

#msform fieldset {
  background: white;
  border: 0;
  border-radius: 10px;
  padding: 20px 30px;
  box-sizing: border-box;
  width: 100%;
  margin: 0 10px;
}

#msform fieldset.active {
  display: block;
}

#msform input,
#msform select {
  padding: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
  width: 100%;
  box-sizing: border-box;
  font-size: 16px;
}

#msform .password-container {
  position: relative;
}

#msform .eye-pass {
  position: absolute;
  right: 15px;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
}

#msform button {
  width: 100%;
  padding: 15px;
  border: none;
  background: #007BFF;
  color: #fff;
  font-size: 16px;
  border-radius: 5px;
  margin: 10px 0;
  cursor: pointer;
}

#progressbar {
  margin-bottom: 30px;
  overflow: hidden;
  counter-reset: step;
}

#progressbar li {
  list-style-type: none;
  color: #ccc;
  text-transform: uppercase;
  font-size: 12px;
  width: 33.33%;
  float: left;
  position: relative;
}

#progressbar li.active {
  color: #000;
}

#progressbar li:before {
  content: counter(step);
  counter-increment: step;
  width: 30px;
  line-height: 30px;
  display: block;
  font-size: 12px;
  color: #333;
  background: #ccc;
  border-radius: 50%;
  margin: 0 auto 5px auto;
}

#progressbar li.active:before {
  background: #007BFF;
  color: #fff;
}
.button-group {
  text-align: center; 
  margin-top: 20px;
}

.btn-inline {
  display: inline-block;      
  margin: 0 10px;             
  padding: 5px 5px;         
  background: #007BFF;
  border: none;
  color: #fff;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
}
.g-recaptcha {
  margin: 15px auto;
  display: flex;
  justify-content: center;
}

.btn-container {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}

button {
  padding: 10px 20px;
  border: none;
  background: #007bff;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background: #0056b3;
}
</style>