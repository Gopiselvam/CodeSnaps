# CodeSnaps
This is to refer the commonly used functionality(code) in Java


**Sort List<String> in ascending order res: List<String>**
  
  List<String> strlist = new ArrayList<>(Arrays.asList(new String[]{"10", "20", "-1", "0.0", "5"}));
  strlist.sort((o1, o2) -> (int) (Double.parseDouble(o1) - Double.parseDouble(o2))  );
  
  (or)
  
  List<String> newliststr = list.stream().sorted( (o1, o2) -> (int) (Double.parseDouble(o1) - Double.parseDouble(o2)) )
                              .collect(Collectors.toList());
  res:  [-1, 0.0, 5, 10, 20]
  
**To convert String[] to Set<Double>**
  
  Set<Double> setdouble = Arrays.stream(strarr).map(Double::new).collect(Collectors.toSet());
  
  
**Querying a DB using EntityManager createQuery and store it to the Map<String, Team>**
  
  Map<String, Team> teamData = new HashMap<>();       // here Team is our custom Entity object
  em.createQuery("select m.team1, count(*) from Match m group by m.team1", Object[].class)
                .getResultList()
                .stream()
                .map(e -> new Team( (String)e[0], (Long)e[1]))    // here Team(String p1, Long p2) is a constructor
                .forEach(team -> teamData.put(team.getTeamName(), team));;
