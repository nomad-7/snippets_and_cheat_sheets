### String
#### RegExp
#### Search for a substring
      var str = "Visit W3Schools!";
      var n = str.search("W3Schools");
      // returns -1 if no match is found, otherwise the first occurance's index

##### Test if string starts with a substring
      const str1 = 'Saturday night plans';

      console.log(str1.startsWith('Sat'));
      // expected output: true

      console.log(str1.startsWith('Sat', 3));
      // expected output: false
