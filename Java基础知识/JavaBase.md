## 1.Lambda列表里存储对象转map
````Java
    List<User> users = new ArrayList<>();
    users.stream().collect(Collectors.toMap(User::getId, User::getName));
````
