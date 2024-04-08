## Motivation & Objectives 
The motivation behind Design-A-Dino derives from how extensive and overwhelming information on the Mesozoic Era can be, especially to younger audiences. The appeal of dinosaurs to children is undeniable, inspiring us to create robust learning experiences. 

## Scope & Deliverables 
Taking an educational approach, we cater our website to younger audiences. In doing so, we focus on providing simplified explanations of complex geologic patterns. This is more concretely explored through investigation of dinosaur trends across locations and Mesozoic periods. 

The outlined objectives of the website are addressed through activity based learning. We use the concept of designing a dinosaur in order to familiarize children with aspects of the creatures and their habitats. This includes developing comprehension of classes, diets, location, and more. 

Through an engaging introduction we are able to expose our audience to much more material, encouraging self exploration. This allows kids to explore analytics, developing critical thinking skills. 

## How we built it
Our website is built using Svelte, JavaScript, CSS, and HTML. The data behind the website comes from a Kaggle dataset of 307 rows found [here](https://www.kaggle.com/datasets/kjanjua/jurassic-park-the-exhaustive-dinosaur-dataset) . After choosing our dataset we then proceeded to clean the data. This included replacing missing values of lengths of 17 dinosaurs by using the length of other rows of the same respective species. The lengths of dinosaurs were then use to create size categories of small, medium, and long. In addition to this, datatypes were corrected along with any other formatting errors. Other column transformations included categorizing countries into continents. To create the data visualizations included in the "Dino Trends" tab, we used Altair to create an interactive map that implements a tooltip. 

## Challenges we ran into
Challenges to the design and implementation process included formatting margins, padding, and embedding visualizations. Implementing the "Dinodex" tab also posed a challenge due to fetching the data from the dataset and formatting the images of the dinosaurs. 

## What we learned
Through this project we learned how to incorporate different languages, frameworks, platforms, and technologies together to form a cohesive website that works as an educative tool for young audiences. Using Figma, we also learned how to plan out designs as a team including cooperating and building upon constructive criticism.  

## What's next for Design-A-Dino
In the future, we would like to expand our website to include more analytics and features that can further develop it into an effective educational tool.
