
## Random Password Generator. 

This project was for week 3 of UCB.
This was premade project where we were to fix and add to JS 
to get a running random password generator.

## Crititeria

---
- GIVEN I need a new, secure password
- WHEN I click the button to generate a password
- THEN I am presented with a series of prompts for password criteria
- WHEN prompted for password criteria
- THEN I select which criteria to include in the password
- WHEN prompted for the length of the password
- THEN I choose a length of at least 8 characters and no more than 128 characters
- WHEN asked for character types to include in the password
- THEN I confirm whether or not to include lowercase, uppercase, numeric, and/or special characters
- WHEN I answer each prompt
- THEN my input should be validated and at least one character type should be selected
- WHEN all prompts are answered
- THEN a password is generated that matches the selected criteria
- WHEN the password is generated
- THEN the password is either displayed in an alert or written to the page

## USER WORKS
---
```python
// Assignment Code
var generateBtn = document.querySelector("#generate"); // generating a button
const upperCaseCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ" // static variables
const lowerCaseCharacters = "abcdefghijklmnopqrstuvwxyz" // static variables
const specialCharactersCase = "!@#$%^&*()_<>=/,'" // static variables
const numbersCase = "1234567890" // static variables
var possibleCharacters = "" // empty string
function generatePassword() { // creating a function
  var passCreate = confirm("Do you want to create a password?");
  if (passCreate == true) {
    var passwordLength = prompt("Enter the length of the password");
    if (passwordLength < 8 || passwordLength > 128) {
      alert("Your password must be atleast 8 characters and no more than 128 characters"); // if statements out of parametetrs
      return generatePassword();
    } else {
      alert("Your password will be " + passwordLength + " charcters long!")
    }
    var upperCase = confirm("Do you want upper case letters?")
    var lowerCase = confirm("Do you want lower case letters?")
    var numbers = confirm("Do you want numbers?")
    var specialCharacters = confirm("Do you want special characters?")
    console.log(passwordLength, upperCase, lowerCase, numbers, specialCharacters);
    if (
      upperCaseCharacters === false &&
      lowerCaseCharacters === false &&
      numbersCase === false &&
      specialCharactersCase === false // if users input nothing
    ) {
      alert("Your password must be one of these character types")
    }
    if (upperCase == true) {
      possibleCharacters = possibleCharacters + upperCaseCharacters;
    }
    if (lowerCase == true) {
      possibleCharacters = possibleCharacters + lowerCaseCharacters;
    }
    if (numbers == true) {
      possibleCharacters = possibleCharacters + numbersCase;
    }
    if (specialCharacters == true) {
      possibleCharacters = possibleCharacters + specialCharactersCase;
    }
    var password = "";
    for (var i = 0; i < passwordLength; i++) {
      var randomIndex = Math.floor(Math.random() * possibleCharacters.length); // this a random generator
      password += possibleCharacters[randomIndex];
    }
    return password;
  }
}
// Write password to the #password input
function writePassword() {
  possibleCharacters = ""; // clear and prevoius entries
  var password = generatePassword(); // function running
  var passwordText = document.querySelector("#password");
  passwordText.value = password;
}
// Add event listener to generate button
generateBtn.addEventListener("click", writePassword);
```