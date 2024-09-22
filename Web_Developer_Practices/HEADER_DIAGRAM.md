# Events Planet UAE: Website Redesign Header Section

** Digital Transformation**

## Introduction:
* This project is all about transforming the current website for Events Planet UAE into a more modern, user-friendly version.
* The redesign will focus on improving how the website looks and works, making it easier to navigate and more engaging for users. 

* The current website is basic and doesn’t give the best user experience. Our job is to upgrade it by adding new features and improving the design.

## Existing Website
* The current website, which you can view here [Events Planet UAE](https://eventsplanetuae.com/), has a basic structure. 
* It provides information but doesn't have the best user experience.
* The layout is simple, and it doesn’t adjust well on different devices like phones or tablets (not responsive).
- Existing Diagram: 

![1 drawio](https://github.com/user-attachments/assets/a48a4dd6-7da6-40cf-bf8b-636b81f1a1f9)

## New Changes Proposed
* We're going to redesign the website to include:

- Better Navigation: A new header (top menu) that makes it easy for users to find what they need.
- Improved Pages: Each page will be better organized with clear headings, images, and important information.
- Responsive Design: The website will look good on any device, whether it's a phone, tablet, or desktop.
  

## High-Level Pages & Components

### Header Section
The header is the top part of the website where users can click on links to go to different pages. 
In this redesign, the header will have these main links:

* **About Us**: This page will explain the company’s history and purpose.
* **Why Choose Us**: This page will highlight why customers should choose Events Planet UAE.
* **Our Expertise**: Details about the company’s skills and services.
* **Our Clients**: This page will show testimonials and reviews from happy clients.
* **Our Activities**:  This page will showcase the recent events and activities organized by the company, providing insights into ongoing and past work.
* **Contact Us**: This page will have a form and contact information for users to get in touch with the company.


**Purpose**: The header serves as the main navigation bar for the website.

* **Structure**:
  * **Left Side**: Contains a logo.
  * **Center With Space**: Links to main pages like "About Us", "Why Choose Us", "Our Expertise", "Our Clients", "Our Activities", "Contact Us".


### Main Pages
Each page has its own route in the app. Below is a breakdown of the main pages and their respective diagrams.

- New Diagram :

![1 drawio (1)](https://github.com/user-attachments/assets/e0019832-42e5-4f47-9139-a1e6640afa53)

### Page Breakdown
Here’s what each of these pages will include:

1. **About Us Page**:
* **Page Components**:
   - Heading: A title explaining the company's story.
   - Images: Pictures that show what the company does.
   - Mission and Vision: Information about the company’s goals and values.

1. **Why Choose Us Page**:
* **Page Components**:
   - Heading: Explaining why this company is the best choice.
   - Description of the company’s unique features and benefits.

1. **Our Expertise Page**:
* **Page Components**:
   - Expertise Heading: A title explaining what the company specializes in.
   - Content: A detailed explanation of the company’s services.
   - Images: Photos showcasing the company’s work.

1. **Our Activities**:
* **Page Components**:
   - Heading: A title explaining the different activities the company performs.
   - Content: Details about the company’s events, workshops, or other activities.
   - Images: Pictures showing the activities or behind-the-scenes moments of events.
   - Videos: Clips showcasing the company’s activities in action.

1. **Our Clients Page**:
* **Page Components**:
   - Testimonials: Quotes from happy clients explaining their experience.
   - Client Images: Pictures showing the events and clients the company has worked with.

1. **Contact Us Page**:
* **Page Components**:
   - Contact Form: A form where users can fill in their name, email, and message.
   - Map: A map showing the company’s location.


#### Pages
In the new Next.js project, routes will be identified as individual pages.

* pages.tsx : This will define the main routes, including.
* /about :  – About Us Page.
* /why-choose-us : – Why Choose Us Page.
* /our-expertise : – Our Expertise Page.
* /our-activities : – Our Activities Page.
* /our-clients : – Our Clients Page.
* /contact : – Contact Us Page.

#### Layout
All the pages on the website will use the same basic structure, which will be set up in a file called layout.tsx. This layout will include the navigation menu at the top and other parts of the website that are reused across all pages.

#### Components
Each diagram represents parts of the website that can be reused, like:

- Header.tsx : This is the main navigation menu that appears at the top of the website. 
It helps users move between pages.

- AboutUs.tsx : This is a component that handles everything shown on the About Us page, such as text and images about the company.

- ContactForm.ts : This is the form on the Contact Us page where users can enter their name, email, and message to get in touch with the company.




#### Navigation Flow Diagram
From the provided diagram:

* The top-level navigation includes links to "About Us", "Why Choose Us", "Our Expertise", "Our Activities", "Our Clients", and "Contact Us."

* Clicking on any of these links will take users to the respective pages:
   - About Us: Contains sections on the company’s mission and vision.
   - Why Choose Us: Lists the company’s unique features points.
   - Our Expertise: Contains heading and detailed and Image.
   - Our Activities: Contains heading and detailed descriptions.
   - Our Clients: Contains testimonials and images.
   - Contact Us: Contains a contact form and a map showing the company’s location.



 
## Diagram Explanation

### Why Do We Need This Diagram?
* The diagram visually explains how the website will be organized. It helps us plan the structure of the website before we start building it.
* This way, developers and non-developers can understand how everything connects and what each page will look like.


### What Needs to Be Done?
1. We will create a header with navigation links to each page (like About Us, Our Expertise, etc.).
1. We will design each page based on the breakdown explained above (titles, content, and images for each).
1. We will ensure that common elements header will appear consistently across all pages.


### What I Have Understood
1. **Navigation**:
* The header will be used to guide users to the different pages on the website.

2. **Page Content**: 
* Each page will have specific content, such as text and images, that will help the user understand what the company offers.

3. **Consistency**:
* The header will be the same on every page, making the site easy to navigate.

4. **Responsive Design**: 
* The website will adjust to different devices (like phones, tablets, and desktops), so it looks good no matter where it’s viewed.



## Development Timeline
Here’s a rough timeline for building the new website:
In 2 weeks: 

* **2 and half Day**: Set up the basic structure of the site with header and logo work (dark and light mode) with documentation.

* **3 Days**: Build the About Us and Why Choose Us pages with documentation.

* **3 Days**: Our Expertise and Our Clients pages with documentation.

* **1 and half Day**: Our Activities page with documentation.

* **2 Day**: Contact Us page with the form and map with documentation.

* **1 Day**: Test everything to make sure the website works well on phones, tablets, and desktops, then launch it.

