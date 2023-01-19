# **Bitesize Introduction**
Zespri is a company selling premium kiwifruit. They coordinate farmers who grow kiwifruit, packhouses that store it and send to retail. Zespri control several licensed [kiwifruit varieties](./Kiwifruit+Varieties+and+Testing.md) and set requirements for all varieties to calculate the payment for batches of fruit that farmers sell them.

Zespri is controlling the sweetness, quality, degree of ripening and other parameters of batches of fruit via the system that we support: the Maturity Clearance System (MCS). [Users of the system](./MCS+Users.md) create Sample Requests and load kiwifruit into testing machines, then MCS compares the values for that kiwifruit and informs the company and the farmer if the quality matches their standards.
## **Testing**
The testing process is somewhat complicated. In 2022, Zespri is using 5 kiwifruit varieties, including green (HE) and gold (GA). Both are tested for weight and sugar content (called BRIX), but the threshold for HE is lower than for GA. In addition, HE is tested for number of seeds while GA is not.

Another parameter for testing is pressure: the bigger it is, the less ripe is the fruit. Zespri uses this parameter to understand which batches of fruit should be shipped for sale and which can wait in storage facilities.

All this information together with other info such as how many fruit is enough for a sample is stored in MCS.
## **Roles**
In addition, there are many user roles with different access rights. For example, a packhouse employee can only see sample requests within their packhouse. Growers cannot see many intermediary steps in testing (the exact state of testing their fruit is deliberately hidden from them).

MCS allows to impersonate different users to see the system with their own eyes.
