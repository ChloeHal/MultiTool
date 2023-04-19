<script>
    const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
    const uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    const numericChars = "0123456789";
    const specialChars = "!@#$%^&*()_+~`|}{[]:;?><,./-=";
    
    let length = 12;
    let includeLowercase = true;
    let includeUppercase = true;
    let includeNumeric = true;
    let includeSpecial = true;
    let password = '';
    
    const generatePassword = () => {
      let chars = '';
      if (includeLowercase) chars += lowercaseChars;
      if (includeUppercase) chars += uppercaseChars;
      if (includeNumeric) chars += numericChars;
      if (includeSpecial) chars += specialChars;
      
      password = '';
      for (let i = 0; i < length; i++) {
        password += chars[Math.floor(Math.random() * chars.length)];
      }
    }
  </script>
  
  <main class="p-4">
    
    <label class="flex items-center mb-2">
      <input type="checkbox" bind:checked={includeLowercase} class="checkbox mr-2">
      Inclure des lettres minuscules
    </label>
    
    <label class="flex items-center mb-2">
      <input type="checkbox" bind:checked={includeUppercase} class="checkbox mr-2">
      Inclure des lettres majuscules
    </label>
    
    <label class="flex items-center mb-2">
      <input type="checkbox" bind:checked={includeNumeric} class="checkbox mr-2">
      Inclure des chiffres
    </label>
    
    <label class="flex items-center mb-2">
      <input type="checkbox" bind:checked={includeSpecial} class="checkbox mr-2">
      Inclure des caractères spéciaux
    </label>
    <label for="length-input" class="mr-2">Longueur :</label>

    <div class="flex items-center input-group  my-4">
        <input type="number" id="length-input" min="4" max="128" bind:value={length} class="w-full px-2 py-1 rounded input input-bordered">
        <button class="btn btn-primary input input-bordered" on:click={generatePassword}>Générer</button>

      </div>
    
    
    {#if password}
    <label for="password-input" class="mr-2">Mot de passe :</label>

    <div class="flex items-center input-group mt-4">
        <input type="text" id="password-input" value={password} class=" px-2 py-1 w-full rounded input input-bordered cursor-pointer" on:click={() => navigator.clipboard.writeText(password)} readonly>
        <button class="btn btn-accent input input-bordered" on:click={() => navigator.clipboard.writeText(password)}>Copier</button>
      </div>
      
    {/if}
  </main>
  