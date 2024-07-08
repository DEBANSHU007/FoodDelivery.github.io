# Online Food Delivery Portfolio

* **Course Name**: Algorithmic Problem Solving
* **Course Code**: 23ECSE309
* **Course Instructor**: Prakash Hegade
* **Name**: Debanshu Behera
* **USN**: 01FE21BCI035
* **University**: KLE Technological University, Hubballi-31

## Table of Contents
* [👋 Introduction](#introduction)
* [📊 Market Analysis](#market-analysis)
* [❓ Why Online Food Ordering as a Topic?](#why-online-food-ordering-as-a-topic)
* [🎯 Objectives](#objectives)
* [💼 Business Cases](#business-cases)
* [🔚 Conclusion](#conclusion)
* [📑 References](#references)

## Introduction
In today's busy world, people are increasingly ordering food online. They can easily order meals from their phones or computers and have the food delivered right to their door. Online food delivery is popular because it saves time, offers a wide variety of restaurant choices, and provides features like order tracking and special deals. As the demand for convenient food delivery grows, companies are creating advanced online systems to manage orders, track deliveries, and keep customers happy. These systems use smart technology to make the food ordering process simple and efficient for both customers and restaurants.

![order-delivery-model](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/6154ce7c-ce39-4da2-8fa6-111a8a6dc32b)


## Market Analysis
The online food delivery market has seen tremendous growth in recent years. According to industry reports, the global food delivery market was valued at over $150 billion in 2021[[1]](https://www.statista.com/outlook/emo/online-food-delivery/india){:target="_blank"} and is expected to grow at a CAGR of 9.8% by 2026[[2]](https://www.grandviewresearch.com/industry-analysis/online-food-delivery-services-market){:target="_blank"}, reaching an estimated $235 billion[[3]](https://www.globenewswire.com/news-release/2022/12/21/2578140/0/en/Online-Food-Delivery-Services-Market-to-Surpass-US-97-29-Billion-by-2032-at-a-Healthy-CAGR-of-9-8-Complete-Study-Report-by-Future-Market-Insights-Inc.html.){:target="_blank"}. To capitalize on this growing market opportunity, food delivery platforms must focus on optimizing their underlying systems and processes. This portfolio focuses on improving the data structures and algorithmic approach used in a food delivery platform. The goal is to create a more efficient and streamlined ordering process, enhance the user experience, and enable more effective delivery logistics.[[4]](https://www.globenewswire.com/news-release/2019/03/29/1788651/0/en/Global-Online-Food-Delivery-Services-Market-Report-2019-Outlook-to-2026-Fierce-Competition-Between-In-house-Third-party-Delivery-Service-Providers-is-Inevitable.html.){:target="_blank"}

![Market](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/77c1d56e-3713-4a8d-a051-7f2819a9f985)



## Why Online Food Ordering as a topic
I have chosen the online food delivery system as the domain for this portfolio because it is a widely used service that plays a significant role in people's daily lives, handling a huge amount of data. This domain presents complex challenges that require the application of advanced data structures and algorithms to optimize various functionalities, such as order management, delivery logistics, personalization, and real-time tracking. Addressing these challenges offers the opportunity to showcase how the strategic use of data structures and algorithms can enhance the overall efficiency and user experience of the food delivery platform, making it a relevant and engaging choice for this portfolio.

## Objectives
This portfolio focuses on improving the food delivery platform by making it work better and more efficiently. The main goals are: 
* Make the ordering process smoother and easier to manage. This includes things like tracking orders and making sure they are fulfilled quickly. 
* Enhance the experience for the people using the platform. This could mean improving features that make it more convenient, personalized, and transparent (so customers can see where their order is). 
* Optimize the delivery process to get the food to customers faster and more reliably. This might involve finding the best routes, reducing delivery times, and improving coordination between the platform, restaurants, and delivery drivers. 
* Usage of advanced data structures and algorithms to power all these improvements. The goal is to take advantage of these algorithms to make the whole food delivery experience better for everyone involved.

## Business Cases

**1. 👨‍👩‍👧‍👦 User Profile management and registerations**

**Use Case**  
* This allow users to create and manage their profiles. Users can input their personal information, manage addresses, and set preferences such as favourite cuisines. The system ensures secure handling of sensitive information like passwords and payment details.

**Challenges**  
* As more people sign up, the system needs to handle all the new accounts without slowing down. Preventing duplicate accounts is important to avoid confusion. Letting users customize their preferences is great, but organizing all that data efficiently is a challenge. Keeping track of who is currently logged in is necessary for a smooth experience.

**Market Benefits**  
* Users will have a better experience and feel more secure, which builds trust. The system can run more smoothly with faster performance and lower costs.

![Userprofile (1)](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/27d5356f-612a-4249-8bd4-7496f3d62b35)


**Data structure and Algorithms used**
* For managing active user sessions, [**linked lists**](./Code/linkedlist.md) can be used to track session information dynamically.
* [**Bloom filter algorithm**](./Code/bloomfilter.md) can be used to quickly check whether an email or username is already in use during registration without having to search through the entire database.[[5]](https://systemdesign.one/bloom-filters-explained/){:target="_blank"}
* [**Binary Search Trees**](./Code/BST.md) to store and organize the user's favorite cuisines and dietary restrictions. BSTs provide efficient searching, insertion, and deletion of these preferences, allowing for quick lookup


**2. 📃 Restaurant Listing and Search**

**Use Case**  
* This displays available restaurants to users based on their location, allowing them to search, filter, and sort options by various criteria such as cuisine, ratings, distance, and price.

**Challenges**  
* Handling large volumes of restaurant data, implementing autocomplete and search suggestions, allowing flexible filtering and sorting, and ensuring data accuracy and consistency are key hurdles that need to be overcome.

**Market Benefits**  
* Implementing an efficient restaurant search and filtering system can significantly enhance the user experience by enabling customers to easily find dining options that match their preferences.

![filter (1)](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/b1b22755-1431-4e48-a744-8ed658b660cb)


**Data structure and Algorithms used**
* [**B-Trees**](./Code/BTree.md) can be used for indexing large database to enable quick search and retrieval.[[6]](https://www.dataquest.io/blog/b-tree-data-structure/){:target="_blank}
* [**Trie (Prefix Tree)**](./Code/trie.md) can be used for implementing autocomplete features in search, making it efficient to retrieve suggestions.
  

**3. 👥 User Related Information caching**

**Use Case**  
* Based on the recent orders in an area, or the most ordered items, or searched items, data could be cached so that the Restaurant Search Service could look up such information from a distributed cache, instead of hitting the search infrastructure, and immediately return few recommendations.

**Challenges**  
* Implementing a caching mechanism to provide personalized restaurant recommendations requires accurately identifying the most relevant data to cache and keeping it up-to-date in a distributed system, which can be complex. 

**Market Benefits**  
* Using a distributed cache for restaurant recommendations makes the service faster and more responsive, leading to happier customers and increased sales. It also reduces costs and helps the system handle more users at once. 

![caching](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/615dd3db-baef-411d-aa0b-b8bd955f0153)


**Data structure and Algorithms used**
* Using Queue data structure we can implement [**Least Recently Used (LRU)**](./Code/LRU.md) or [**Least Frequently Used (LFU)**](./Code/LFU.md) algorithm, or a combination of both can be our cache eviction strategy for our use case.
  

**4. 🛣️Route planning (Finding shortest path)**

**Use Case**  
* Identifying the shortest route in a food delivery system means finding the quickest path for delivery drivers to reach multiple destinations, optimizing time and efficiency.

**Challenges**  
* Identifying the shortest route in a food delivery system involves challenges such as accurately predicting traffic conditions and potential delays, handling dynamic changes in delivery requests, and ensuring real-time updates to routes based on new orders or cancellations. It requires sophisticated algorithms to consider multiple variables like delivery time windows, driver availability, and road conditions.

**Market Benefits**  
* Optimizing the shortest routes in a food delivery system enhances delivery speed and efficiency, leading to quicker delivery times and increased customer satisfaction. This efficiency reduces fuel and operational costs for drivers, contributing to lower overall expenses.

![shortestpath](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/b395a1e6-24ef-4b1b-95c8-72db250dfca9)

**Data structure and Algorithms used**
* Online Food delivery system can use algorithms like [**Dijkstra’s**](./Code/Dijkstra's.md) to determine the shortest route between a restaurant and a client. Based on the weights given to the edges, these algorithms iterate over the graph and determine the shortest path. The Dijkstra Algorithm selects the node with the smallest cumulative weight iteratively until it reaches the target, which is the customer, starting at the source node (restaurant) and exploring all nearby nodes.[[7]](https://locall.host/how-zomato-algorithm-works/){:target="_blank"}
* Algorithms like Dijkstra's and [**A*searching algorithm**](./Code/Astarsearch.md) can be used to determine the most efficient path between two geographic locations based on factors such as distance, time, and traffic conditions.


**5. 🍽️ Nearest Restaurant Searching**

**Use Case**  
* Nearest restaurant searching involves enabling users to quickly locate dining options based on their current location or specified radius. This functionality is crucial for mobile apps and websites offering food delivery or dining recommendations by utilizing location based services.

**Challenges**  
* Implementing nearest restaurant searching faces challenges such as accurately updating and maintaining location data for restaurants, ensuring the reliability and precision of location-based services across different devices and platforms, and managing privacy concerns related to user location information.

**Market Benefits**  
* Enabling users to quickly find the nearest restaurants through location-based searching enhances user experience by providing convenience and personalized dining options.By suggesting nearby restaurants at the right moment, businesses can encourage more spontaneous dining choices and increase how often people place orders.

![nearestrest](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/76a0f46c-c68a-4800-af03-956f9544fe3a)


**Data structure and Algorithms used**
* To find restaurants within a certain radius or determine the nearest restaurant to a user's location spatial indexing techniques like [**KD Trees**](./Code/Kdtree.md)[[8]](https://www.geeksforgeeks.org/search-and-insertion-in-k-dimensional-tree/){:target="_blank"} or [**Quad trees**](./Code/Quadtree.md) can be used to efficiently store and query geospatial data. These algorithms can minimize the time and computational resources needed to perform operations on large datasets.
  

**6. 🛵Streamlining Delivery paths**

**Use Case**  
* Streamlining delivery paths in food delivery involves optimizing routes to ensure quick and efficient order fulfilment. This includes minimizing travel distances, considering multiple deliveries per trip, and adapting routes in real-time based on traffic and delivery priorities, all to enhance delivery speed.

**Challenges**  
* Streamlining delivery paths in food delivery presents challenges such as accurately predicting and adapting to dynamic traffic conditions, coordinating multiple deliveries to minimize delays and optimize efficiency, and integrating real-time data updates into route planning algorithms.

**Market Benefits**  
* By optimizing routes, businesses can reduce operational costs associated with fuel and vehicle maintenance, while increasing the number of deliveries per driver shift. This efficiency not only enhances overall service reliability but also supports scalability, allowing businesses to handle higher order volumes during peak times without compromising delivery speed or quality.

![VRP](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/a545b0fe-20bb-47ae-8a1a-7d301c45b48a)


**Data structure and Algorithms used**
* Route Optimization Algorithms such as the [**Vehicle Routing Problem (VRP) algorithms**](./Code/VRP.md)[[9]](https://trackobit.com/blog/vehicle-routing-problem-decoded-what-why-and-how){:target="_blank"} and the [**Travelling Salesman Problem (TSP)**](./Code/TSP.md) solver using Dynamic Programming, to optimize numerous deliveries in addition to the shortest way. These algorithms take into account things like consumer preferences, vehicle capacity, and delivery window times.
  

**7. 📜Displaying Menu**

**Use Case**  
* This enables customers to conveniently explore and select menu items from list of restaurants. It presents the restaurant's menu in an organized manner, categorizing dishes and providing detailed descriptions, prices, and images for each item. Additionally, the menu should allow customers to customize their orders by choosing options like size, add-ons, or special instructions.

**Challenges**  
* Enabling customers to explore and select menu items from various restaurants faces challenges such as maintaining accurate and up-to-date menu information across different platforms, ensuring consistency in item availability and pricing.

**Market Benefits**  
* By presenting organized menus with detailed descriptions, prices, and images, businesses can effectively showcase their offerings and attract more customers. Providing customization options like size variations and add-ons enhances personalization.

![Menu display](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/855aafb5-37ea-4ae7-847c-0d6fed45c825)


**Data structure and Algorithms used**
* [**segment trees**](./Code/segmenttree.md)[[10]](https://www.sanfoundry.com/cpp-program-to-implement-segment-tree/){:target="_blank"} can be used to efficiently handle range queries and updates, such as filtering menu items by price ranges or ratings. This data structure allows for fast querying and updating of aggregated information over intervals.


**8.  💳Payment Processing**

**Use Case**  
* The online food delivery platform offers a comprehensive payment solution that supports a variety of payment methods, including credit/debit cards, digital wallets, and net banking, this use case ensures secure and reliable transactions. Additionally, the system provides the option for customers to save their preferred payment details, enabling faster and more convenient checkout experiences for repeat orders.

**Challenges**  
* Implementing a comprehensive payment solution for online food delivery faces challenges such as ensuring efficient security measures to protect sensitive payment information against cyber threats and fraud.

**Market Benefits**  
* Implementing a comprehensive payment solution for online food delivery offers significant market benefits by enhancing customer convenience and trust. Supporting diverse payment methods such as credit/debit cards, and net banking accommodates varying customer preferences, expanding the platform's accessibility and user base.

![paymentprocess (1)](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/21ddaaa8-eeea-4465-9a65-c90f7546ffaf)


**Data structure and Algorithms used**
* We can implement [**Merkle Trees**](./Code/merkletree.md)[[11]](https://www.geeksforgeeks.org/introduction-to-merkle-tree/){:target="_blank"} Data structure to efficiently verify the consistency of transaction data, for maintaining and validating the history of payment activities on the system. This also helps ensuring the security and reliability of the payment processing system for both customers and the platform.


**9. 🔔Notification and Alerts**

**Use Case**  
* This use case sends push notifications to users about order status updates, promotions, or other important information. Ensures users are kept informed without having to check the app continuously.

**Challenges**  
* Sending push notifications in an online food delivery platform presents challenges such as ensuring timely and accurate delivery of notifications across various devices, managing user preferences for notification frequency and content to avoid overwhelming users, Maintaining the balance between informative updates and promotional messages while respecting user privacy.

**Market Benefits**  
* By keeping users informed about order status updates and promotions in real-time, system can improve customer experience and reduce customer enquiries about order progress. This proactive communication not only increases transparency but also encourages repeat orders and boosts customer loyalty.

![notification](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/e322004a-d445-40a8-9c08-1534a9554d40)


**Data structure and Algorithms used**
* A [**priority queue**](./Code/priorityqueue.md)[[12]](https://www.geeksforgeeks.org/priority-queue-set-1-introduction/){:target="_blank"} or [**Min Heap**](./Code/minheap.md) can be used to prioritize the notifications based on factors like order status, urgency, or user preferences. This allows the system to process and send the notifications in the correct order, ensuring users receive the most important updates first.
  

**10. 🗺️Providing Location Based Services**

**Use Case**  
* This functionality incorporates geofencing capabilities to provide location-based services and notifications to users. By defining virtual geographic boundaries, the system can detect when a user enters or exits a specific area and trigger relevant actions, such as sending targeted promotions or offering delivery options from nearby restaurants.

**Challenges**  
* Incorporating geofencing capabilities in an online food delivery platform involves challenges such as ensuring accurate and reliable location detection across different devices and environments.

**Market Benefits**  
* Incorporating geofencing capabilities in an online food delivery platform offers significant market benefits by enhancing personalized user experiences and increasing operational efficiency. By leveraging location-based services, businesses can send targeted notifications and promotions to users when they are near participating restaurants.
  
![locationbasedservices](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/6ae9f14c-8070-4d75-b231-04bf76389822)

**Data structure and Algorithms used**
* The online food delivery platform can implement [**Quad Trees**](./Code/Quadtree.md) based algorithms to efficiently store and manage spatial data for geofencing queries.


**11. 🔃 Load Balancing for handling large volume of requests**

**Use Case**  
* Load balancing needed to be implemented efficiently for online food delivery system due to the high volume of user requests and the need for fast, reliable service. Effective load balancing ensures that the system can handle peak loads, provide quick responses, and maintain a smooth user experience.

**Challenges**  
* Efficiently implementing load balancing in an online food delivery system faces challenges such as dealing with unpredictable traffic spikes, ensuring fair distribution of load among servers to prevent any single server from becoming a bottleneck, and maintaining low latency for real-time order processing.

**Market Benefits**  
* Effective load balancing in an online food delivery system enhances user satisfaction by ensuring fast and reliable service, even during peak times, which can lead to increased order volume and customer loyalty.
  
![loadbalancing1](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/d387ad90-bb62-406c-a7a4-797063e07590)

**Data structure and Algorithms used**
* [**Least Connection load balancing**](./Code/leastconnectionloadbalancer.md) algorithm can be used to direct traffic to the server with the fewest active connections.[[13]](https://www.geeksforgeeks.org/load-balancing-algorithms/){:target="_blank"}
* [**Geographic Load Balancing algorithm**](./Code/geaographicloadbalancer.md) can be used to route traffic based on the geographic location of the user.
Combination of Geographic Load Balancing algorithm with Least Connection algorithm can provide an optimal solution.

![loadbalancing2](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/08e7c6ae-be00-40ec-8343-ae3a62dccf9f)



**12. 🏆 Loyalty Schemes Handling**

**Use Case**  
* This use case offers a loyalty program that rewards repeat customers with points or other benefits. This feature motivate users to continue using the service, promoting customer loyalty and increasing the platform's user retention and engagement.

**Challenges**  
* Implementing a loyalty program in an online food delivery platform involves challenges such as designing a rewards structure that  ensure fairness and transparency in point accumulation and redemption processes.

**Market Benefits**  
* Implementing a loyalty program in an online food delivery platform provides significant market benefits by improving customer loyalty and increasing user retention. By rewarding repeat customers with points or benefits, businesses can increase continued use of their services, leading to increased order frequency.

![loyaltypoints (1)](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/10cc5054-1f7c-4e82-bc01-7a24b4a54476)


**Data structure and Algorithms used**
* The online food delivery platform can utilize a [**Fenwick Tree**](./Code/fenwick.md)[[14]](https://www.baeldung.com/cs/fenwick-tree){:target="_blank}, also known as a Binary Indexed Tree, to efficiently manage and update the loyalty points earned by customers. 


**13. 🤳Customer Reviews and Ratings**

**Use Case**  
* This use case allows customers to leave reviews and ratings for the restaurants they order from. This feedback is displayed to other users, helping them make informed decisions about which restaurants to choose. The platform uses this customer review data to improve the overall quality of the restaurants and menu items offered on the platform.

**Challenges**  
* Enabling customers to leave reviews and ratings for restaurants involves challenges such as managing a large volume of user-generated content to ensure authenticity and relevance while preventing fake reviews and spam.

**Market Benefits**  
* By allowing customers to share their experiences and opinions, businesses can attract new users who rely on peer feedback to make informed decisions. Positive reviews and high ratings can serve as powerful endorsements, driving customer acquisition and increasing order volumes.

![review](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/5df8889a-8610-4d49-bf24-2a6ffed3b895)


**Data structure and Algorithms used**
* The online food delivery platform can use a [**Trie data structure**](./Code/trie.md) to efficiently store and search through user-generated reviews. This allows for quick prefix-based searches, autocomplete suggestions, and partial matching of review text, enabling users to easily find relevant reviews.
* The platform can implement [**Min-Heaps**](./Code/minheap.md) or [**Max-Heaps**](./Code/maxheap.md) to maintain a dynamic collection of reviews based on their ratings. This allows for the quick retrieval of the best or worst rated reviews.



**14. 💁Customer Support**

**Use Case**  
* Customer support functionality in an online food delivery platform ensures users receive timely assistance through multiple channels such as chat, email, or phone. It helps resolve various issues related to orders, payments or complain related queries.

**Challenges**  
* Customer support functionality in an online food delivery platform faces challenges such as managing high volumes of enquiries during peak times, ensuring consistency and accuracy in responses across different support channels, and maintaining response times that meet user expectations.

**Market Benefits**  
* By offering timely assistance and resolving issues related to orders, payments, and complaints, businesses can improve overall service reliability and customer retention. Responsive customer support also helps in mitigating negative feedback and managing reputation effectively.

![customersupport (1)](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/80c1c82a-8e78-478b-9d64-5512e10fa0a5)



**Data structure and Algorithms used**
* [**Trie Data Structures**](./Code/trie.md) can be used for managing and searching through large volumes of support articles and FAQs efficiently.
* Balanced Binary Tree ([**AVL Trees**](./Code/AVLTree.md) or [**Red Black Trees**](./Code/RBT.md) can be used for quick lookup of responses.


**15. ⏲️Real Time Order Tracking**

**Use Case**  
* The platform provides real-time updates on order status, showing users the progress from preparation through to delivery. Users can track the delivery person's location on a map and receive estimated arrival times.[[15]](https://medium.com/@swarnavo.pramanik1701/design-lld-a-system-for-online-food-ordering-and-delivery-like-zomato-93b70cc79a3f){:target="_blank"}

**Challenges**  
* Real-time updates on order status and tracking delivery person present challenges such as Coordinating dynamic changes in delivery routes, managing and displaying real-time location data in a user-friendly interface while maintaining data privacy and security.

**Market Benefits**  
* By allowing users to monitor their orders' progress and track delivery drivers on a map, businesses can improve trust and reliability. This capability reduces uncertainty and enhances user convenience, potentially reducing customer inquiries and support requests.

![realtimetracking](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/62ed1f3b-7d18-4e9a-9e0a-6db5b40eb1d5)


**Data structure and Algorithms used**
* [**KD trees**](./Code/Kdtree.md) or [**R-Tree**](./Code/Rtree.md)[[16]](
https://www.bartoszsypytkowski.com/r-tree/){:target="_blank"} can be used efficiently store and query spatial data, useful for managing the locations of multiple delivery drivers.


## Conclusion

This portfolio shows how advanced algorithms can improve online food delivery systems. By using smart data structures and algorithms, we can make ordering food easier, faster, and more reliable. This helps customers get their meals quicker, makes the process smoother for restaurants, and ensures delivery drivers have the best routes. Overall, these improvements can make the food delivery experience better for everyone involved.


## References
[1] “Topic: Online Food Delivery - India,” Statista, Apr. 24, 2024. https://www.statista.com/outlook/emo/online-food-delivery/india  <br><br>
[2] “Online Food Delivery Services Market Size, Share & Trends Analysis”, GrandViewResearch,2021. https://www.grandviewresearch.com/industry-analysis/online-food-delivery-services-market  <br><br>
[3] "Online Food Delivery Services Market to Surpass US$ 97," GlobeNewswire, 2022. https://www.globenewswire.com/news-release/2022/12/21/2578140/0/en/Online-Food-Delivery-Services-Market-to-Surpass-US-97-29-Billion-by-2032-at-a-Healthy-CAGR-of-9-8-Complete-Study-Report-by-Future-Market-Insights-Inc.html.  <br><br>
[4] "Global Online Food Delivery Services Market Report, 2019: Outlook to 2026 - Fierce Competition Between In-house & Third-party Delivery Service Providers is Inevitable," GlobeNewswire, 2019.  <br><br>https://www.globenewswire.com/news-release/2019/03/29/1788651/0/en/Global-Online-Food-Delivery-Services-Market-Report-2019-Outlook-to-2026-Fierce-Competition-Between-In-house-Third-party-Delivery-Service-Providers-is-Inevitable.html.  <br><br>
[5] “Topic: Bloom Filters Explained,” SystemDesign, Mar. 06, 2023. https://systemdesign.one/bloom-filters-explained/  <br><br>
[6] Mehdi Lotfinejad,”How to implementa B-Tree Data Structure,”DataQuest, Oct. 19, 2022. https://www.dataquest.io/blog/b-tree-data-structure/  <br><br>
[7] “Topic: Unlocking the Secrets of Zomato’s Algorithm,” localhost,  Jun. 3, 2022.https://locall.host/how-zomato-algorithm-works/   <br><br>
[8] GeeksforGeeks, “Search and Insertion in K Dimensional tree,” GeeksforGeeks, Jun. 13, 2023. https://www.geeksforgeeks.org/search-and-insertion-in-k-dimensional-tree/  <br><br>
[9] Tithi Agarwal, “Vehicle Routing Problem (VRP): An Overview and Solution Strategies”, TrackoBit, Dec. 12, 2023. https://trackobit.com/blog/vehicle-routing-problem-decoded-what-why-and-how  <br><br>
[10] Manish, “C++ program to implement segment Tree,” Sanfoundry, May 19, 2022. https://www.sanfoundry.com/cpp-program-to-implement-segment-tree/  <br><br>
[11] GeeksforGeeks, “Introduction to Merkle Trees”, GeeksforGeeks, May. 03, 2024. https://www.geeksforgeeks.org/introduction-to-merkle-tree/  <br><br>
[12] GeeksforGeeks,”What is Priority Queue, Introduction to Priority Queue”,GeeksforGeeks, Jan. 11, 2023. https://www.geeksforgeeks.org/priority-queue-set-1-introduction/  <br><br>
[13] GeeksforGeeks,”Types of Load Balancing Algorithm”, GeeksforGeeks, Jan. 31,2024. https://www.geeksforgeeks.org/load-balancing-algorithms/  <br><br>
[14] Gang Wu, “Understanding Fenwick Tree,” Baeldung, Jun. 2,2022. https://www.baeldung.com/cs/fenwick-tree  <br><br>
[15] Swarnavo Pramanik, “Design (LLD) a system for online food ordering and delivery like Zomato”, Medium,Apr. 2, 2024. https://medium.com/@swarnavo.pramanik1701/design-lld-a-system-for-online-food-ordering-and-delivery-like-zomato-93b70cc79a3f  <br><br>
[16] Bartosz Sypytkowski, “R-Tree: algorithm for efficient indexing of spatial data”, bartoszsypytkowski, April 29, 2022.https://www.bartoszsypytkowski.com/r-tree/  <br><br>




