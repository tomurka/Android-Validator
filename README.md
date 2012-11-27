Android-Validator
=================

Form Validator Library for Android

Presentation
------------

Form Validator Library for Android is based on [Zend_Validator](http://framework.zend.com/manual/1.12/en/zend.validate.introduction.html, "Title") coded in PHP. This library is intended to simplify and streamline the code to validate a form Android. For the moment, the form can just handle the **EditText**. Other elements will emerge in future versions.

### License

* [Apache Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

Use
---

Form Validator Library is composed of 3 members : 
-   **Form :** Contains all beings validates to treat. This is the Form that manages the display of error messages in the various elements.
-   **Validate :** Contains all the validators to be treated for a given element.
-   **Validator :** Can define a validation rule.

### Validator

The validator is basic class for this library. It contains specific validation rules. To instanciate validator, you just have to do this (EmailValidator for example):

    new EmailValidator(context);

For some validators, functions can change the validation rules. The validator currently contains three basic validation rules:
+   **EmailValidator** : Ensures that the field does contain a email address. You can also define a regex to check for a particular domain name with the function `setDomainName(DomainRegexp)`. Example for **gmail.com** domain : `setDomainName("gmail\\.com")`. 
+   **NotEmptyValidator** : Ensures that the field is not empty.
+   **UrlValidator** : Ensures that the field is a valid url.
+   **Custom Validator** : You can create your own Validator. To do this, you can just create class extends Validator :

    `public class CustomValidator extends Validator 
    {
        private int mErrorMessage = R.string.validator_custom; // Your custom error message
        public CustomValidator(Context c) {
            super(c);
        }
        
        @Override
        public boolean isValid(Object value) {
            // Your validation Test is here.
            // Retour true if it's correct, false if it's incorrect
            return true;
        }
        
        @Override
        public String getMessage() {
            return mContext.getString(mErrorMessage);
        }
    }`
    
### Validate
