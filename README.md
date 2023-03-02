# validator

A simple and light weight php validator

## Define validation rules

Each field has one or more validation rules. For example, the email field is required and must be a valid email address, so the email field has two rules:

- required;
- email;

The username is required and between 3 and 255 characters. Also, it should contain only letters and numbers. Therefore, the username field has three rules:

required
between 3 and 20 characters
alphanumeric
To define rules for fields, you can define a $fields array like this:

$fields = [
'email'=> 'required | email',
'username' => 'required | alphanumeric | between: 3,255
];
Code language: PHP (php)
Each element in the $fields array has the key as the field name and value as the rules. You use the | character to separate two rules.

If a rule has parameters, e.g., between: 3, 25, you use the : character to separate the rule name and its parameters. Also, we use the comma , to separate two parameters.

You’ll create the following rules:

<table><thead><tr><th>Rule</th><th>Rule name</th><th>Parameter</th><th>Meaning</th></tr></thead><tbody><tr><td>required</td><td>required</td><td>No</td><td>The field is set and not empty</td></tr><tr><td>alphanumeric</td><td> alphanumeric</td><td>No</td><td>The field only contains letters and numbers</td></tr><tr><td>email</td><td>email</td><td>No</td><td>The field is a valid email address</td></tr><tr><td>secure</td><td>secure</td><td>No</td><td>The field must have between 8 and 64 characters and contain at least one number, one upper case letter, one lower case letter, and one special character. This rule is for the password field.</td></tr><tr><td>min: 3</td><td>min</td><td>An integer specifies the minimum length of the field</td><td>The length of the field must be greater than or equal to min length, e.g., 3</td></tr><tr><td>max: 255</td><td>max</td><td>An integer specifies the maximum length of the field</td><td>The length of the field must be less than or equal to min length, e.g., 255</td></tr><tr><td>same: another_field</td><td>same</td><td>The name of another field</td><td>The field value must be the same as the value of the another_field</td></tr><tr><td>between: min, max</td><td>between</td><td>min and max are integers that specify the minimum and maximum length of the field</td><td>The length of the field must be between min and max.</td></tr><tr><td>unique: table, column</td><td>unique</td><td>column and table in a relational database. Or field and collection in a NoSQL database</td><td>The field value must be unique in the column of the table in a database</td></tr></tbody></table>

$fields = [
'firstname' => 'required, max:255',
'lastname' => 'required, max: 255',
'address' => 'required | min: 10, max:255',
'zipcode' => 'between: 5,6',
'username' => 'required | alphanumeric | between: 3,255 | unique: users,username',
'email' => 'required | email | unique: users,email',
'password' => 'required | secure',
'password2' => 'required | same:password'
];
