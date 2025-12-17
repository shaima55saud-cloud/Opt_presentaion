# Opt_presentaion

# مقدمة:


- السلام عليكم ورحمة الله وبركاته. معكم شيماء الرويشد، اليوم بشرح تصميم خوارزمية Simulated Annealing الي استخدمناها لحل Traveling Salesman Problem.
- ى Simulated Annealing هي خوارزمية stochastic single-solution تعتمد على العشوائية اثناء البحث، وهذا كان مهم بالنسبة لنا عشان تكون المقارنة عادلة مع الـ Genetic Algorithm.

# البداية:

- بدأنا الخوارزمية بحل عشوائي يمثل tour كامل يمر على جميع cities مرة وحدة. هذا الحل يكون نقطة البداية للبحث.

- بدل ما نغيّر المسار بالكامل، نعتمد على تغييرات بسيطة. في كل خطوة نولد neighbor solution باستخدام swap operator. هذا الأسلوب يحافظ على الحل كـ valid permutation وفي نفس الوقت يسمح باستكشاف حلول جديدة.

- بعد ما نولد الحل الجديد، يتم تقييمه. إذا كان الحل أفضل من الحل الحالي، يتم قبوله مباشرة. وإذا كان أسوأ، ممكن يتم قبوله باحتمالية تعتمد على قيمة الـ temperature الحالية. هذا الأسلوب يساعد الخوارزمية إنها ما تعلق في local minima في المراحل المبكرة من البحث.

- بعد ذلك، تقل الـ temperature تدريجيًا باستخدام geometric cooling schedule. في البداية يكون الاستكشاف كبير، ومع انخفاض temperature تقل احتمالية قبول الحلول الأسوأ ويتركز البحث على تحسين الحل الحالي.

- عند كل temperature، ننفّذ عدد ثابت من inner iterations حتى نسمح للخوارزمية باستكشاف عدد كافي من الحلول قبل الانتقال للمرحلة التالية.

- وأخيرًا، رغم إن Simulated Annealing تعتبر memory-less algorithm، قمنا بتتبع أفضل best solution تم الوصول له أثناء التنفيذ، عشان نضمن إن النتيجة النهائية تمثل أفضل tour تم العثور عليه خلال كامل البحث.


# Introduction
- Hello everyone. My name is Shaimaa Al-Ruwayshed. Today, I will explain the design of the Simulated Annealing algorithm that we used to solve the Traveling Salesman Problem (TSP).

- Simulated Annealing is a random, single-solution optimization algorithm. It uses randomness during the search process. We chose it to make a good comparison with the Genetic Algorithm, since both methods are stochastic.

# Algorithm Design
- We start the algorithm with a random tour that visits all cities once. This tour is the initial solution.

- Instead of changing the whole tour, we make small changes. In each step, we create a new solution using a swap operator, where we swap two cities. This keeps the tour valid and helps explore new solutions.
  
## After creating the new solution, we evaluate it.
If the new solution is better, we accept it directly.
If it is worse, we may still accept it based on the current temperature.
This helps the algorithm avoid getting stuck in local minima.

## The temperature is reduced using a geometric cooling schedule.
- At high temperature, the algorithm explores more solutions.
- At low temperature, it focuses on improving the current solution.

At each temperature level, we run a fixed number of inner iterations to allow enough exploration before moving to the next temperature.

Finally, even though Simulated Annealing does have memory, we track the best solution found during the entire run to ensure the final result is the best tour discovered.
