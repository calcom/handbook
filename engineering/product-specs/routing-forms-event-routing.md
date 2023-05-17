# ✏ Routing Forms/Event Routing

### <mark style="color:orange;">Further dicussions would happen on</mark> [<mark style="color:orange;">RFC</mark>](https://github.com/calcom/cal.com/issues/2781) <mark style="color:orange;">and once we ship it, it would have final implementation details</mark>

### **Why Routing Forms**

..........

### **Types of Routing**

* Route to particular cal link.
* Route to booking with a particular member of a team event that's the best match. It can be like a new addition to Scheduling Type options (Collective, Round Robin) - _<mark style="color:red;">Calendly doesn't seem to have it.</mark>_
* Route to external URL e.g. if requirements for a meeting don’t meet
* Route to a Page with a custom message e.g. Thank you for your interest but we aren't ready to serve you yet.

### Features

* Support in both embed and direct Cal link.
* Enrich using the data directly provided by the user or any plugin(e.g. in embed there can be a plugin that can use the data available to the website about the user)  and then use the data to decide which team member to route to.
* Duplicate a Routing Form
* Export Results
  * As there would be more data that can be useful for the organizer to learn about the booker before the meeting, this is important.
* Questions can be marked required/optional

#### **Questions?**

* Do we use the private URL for it or make it work directly with the public Cal Link ?&#x20;

## Components

<details>

<summary>Form Builder with logic(UI)</summary>

**Purpose**

* To create questions.

**Types of Questions**

* Name - _<mark style="color:red;">Calendly doesn't allow routing based on it</mark>_
  * _Flavours_
    * Single Input Box&#x20;
    * Full Name, Middle Name, LastName
* Email&#x20;
  * _<mark style="color:orange;">Operators</mark> - Operates on Email domain only(probably)_
    * includes
    * doesn't include
* Phone Number - _<mark style="color:red;">Calendly doesn't allow routing based on it</mark>_
* Short Text - _<mark style="color:red;">Calendly doesn't allow routing based on it</mark>_
* Long Text - _<mark style="color:red;">Calendly doesn't allow routing based on it</mark>_
* Radio
  * _<mark style="color:orange;">Operators</mark>_
    * is&#x20;
    * is not
* Single Select
  * _<mark style="color:orange;">Operators</mark>_
    * is&#x20;
    * is not
* Multi Select <mark style="color:green;">\[Not in Calendly]</mark>
* Checkbox <mark style="color:green;">\[Not in Calendly</mark>

</details>

<details>

<summary>Routing Module(UI)</summary>

* <mark style="color:green;">\[Not in Calendly]</mark> It can allow the user to choose the route to a different next question based on previous answers
  * Software Engineer →Go to Question(To Learn Programming Language) → C++(answered) -> Book a meeting with a C++ Expert
  * Designer → Go to Question(Learn which Design tool) → Answered(Figma) -> Book meeting with a Figma expert

**Useful Open Source Projects**

* A query builder that can export to JSON Logic [https://github.com/ukrbublik/react-awesome-query-builder](https://github.com/ukrbublik/react-awesome-query-builder)
  * **Pros**
    * Provides Drag and Drop of conditions
    * Many operators are supported based on data type
    * Grouping Support Group1 = A || B; Group2=C || D and Group1 && Group2
    * Declarative UI builder
    * Automation Tests
  * **Cons**
    * Would need to work on UI.
    * Doesn't use tailwind.
    * Not well maintained. We can just fork from it
    * Automation tests in Karma&#x20;
* JSON logic JS - Can evaluate JSON logic to true/false [https://github.com/jwadhams/json-logic-js#readme](https://github.com/jwadhams/json-logic-js#readme)

</details>

<details>

<summary>Team Member - Attributes set and update (UI)</summary>



</details>

### **MoM 12th May**

* Ciaran to check Calendly and Deel to understand what should be our MVP
* Calendly is more custom and doesn't consider Calendly Team Member attributes

**Sources:**

[Calendly Routing Forms](https://www.loom.com/share/994f4d7e48cc40d49bd6729298670719)
