# CodeSnaps
This is to refer the commonly used functionality(code) in Java

# Collections

## Sort List<String> in ascending order res: List<String>
  ```
  List<String> strlist = new ArrayList<>(Arrays.asList(new String[]{"10", "20", "-1", "0.0", "5"}));
  strlist.sort((o1, o2) -> (int) (Double.parseDouble(o1) - Double.parseDouble(o2))  );
  ```
  (or)
  ```
  List<String> newliststr = list.stream().sorted( (o1, o2) -> (int) (Double.parseDouble(o1) - Double.parseDouble(o2)) )
                              .collect(Collectors.toList());
  res:  [-1, 0.0, 5, 10, 20]
  ```
## To convert String[] to Set<Double>
  ```
  Set<Double> setdouble = Arrays.stream(strarr).map(Double::new).collect(Collectors.toSet());
  ```
  
## Querying a DB using EntityManager createQuery and store it to the Map<String, Team>
  ```
  Map<String, Team> teamData = new HashMap<>();       // here Team is our custom Entity object  
  em.createQuery("select m.team1, count(*) from Match m group by m.team1", Object[].class)  
                .getResultList()      
                .stream()        
                .map(e -> new Team( (String)e[0], (Long)e[1]))    // here Team(String p1, Long p2) is a constructor <br/>
                .forEach(team -> teamData.put(team.getTeamName(), team)); 
  ```
  
 ## Convert List<String> to String
 
 ```
 String.join(System.lineSeparator(), list);
 ```
 Here line separator will print each element in separate line.<br/>
 [elem1, elem2, elem3] <br/>
 will be converted to <br/>
 elem1 <br/>
 elem2 <br/>
 elem3 <br/>
  
 ## Making n number of copies of a same element into collection
  ```
  Collections.nCopies(n, "element");
  Collections.nCopies(3, "Hi");     // [Hi, Hi, Hi]
  String.join("", Collection.nCopies(indentSize * n, " "));   // will create indentation for HTML tags
  ```
 ## Sorting Map based on values
  {"num1"=10,"num2"=8,"num3"=20,"num4"=-15,"num5"=1}  will be sorted to {"num1"=-15,"num2"=1,"num3"=8,"num4"=10,"num5"=20}
  ```
  LinkedHashMap<String, Integer> result = sourcemap.entrySet().stream()
                                                   .sorted(Comparator.comparing(Map.Entry::getValue))
                                                    .collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue, (oldValue, newValue) -> newValue, LinkedHashMap::new ));
  ```
 
# String  
## String.format
  ```
  String.format("<li> %s </li>", str); 
  String.format("2.0f", 64.3493872);      // output: "64"
  ```
## remove duplicate characters from String
  ```
  String str = "12311145622";
  String res = Arrays.stream(str.split("")).distinct().collect(Collectors.joining);
  System.out.println(res);      // op: 123456
  ```
  
# System things
## Get the root directory of java program
 ```
 System.getProperty("user.dir");
```

# Random
  ## generate random number between min, max
  ```
  (int)(Math.random() * (max-min+1)+min)      // min 50; max 100 => random integer between 50<= random <=100
  new Random().nextInt(num)                   // if num = 100  => will generate random integer between 0 <= num < 100
  new Random().nextInt(max - min) + min + 1     // if min = 1000 and max = 1100 => will generate random number between 1000 <= num <=1100
  ```

