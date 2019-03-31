**Replace Parameter with Explicit Methods**

When a method is split into parts with decisions based on the parameters.
To make our intent clear on what actually method does, we should extract functionalities into their respective methods.
And then we call them instead of old method.


**Example**

_Issue_

```csharp
void SetAgreementsValue(string agreementName, bool isAgree)
{
  if(agreementName == "privacy")
  {
    this.IsAgreeWithPrivacy = isAgree;
    return;
  }
  if(agreementName == "cookies")
  {
    this.IsAgreeWithCookies = isAgree;
    return;
  }
}

SetAgreementsValue("privacy", true);
SetAgreementsValue("cookies", true);
```

_Refactoring_

```csharp
void SetPrivacyAgreement(bool isAgree)
{
  this.this.IsAgreeWithPrivacy = isAgree;
}

void SetCookiesAgreement(bool isAgree)
{
  this.this.IsAgreeWithCookies = isAgree;
}

// Invoke these methods however you want;
// either with `if` statements or `polymorphism`.
SetPrivacyAgreement(true);
SetCookiesAgreement(true);
```

Another good example on why we should refactor this way:
`setValue("engineEnabled", true)` -> `startEngine()`.
Latter states intent very clearly.

This technique eliminates smells
* Switch statements
* Long method

Similar refactorings
* Replace conditional with polymorphism

Anti refactoring
* Parameterize method