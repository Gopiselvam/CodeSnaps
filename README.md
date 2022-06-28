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
