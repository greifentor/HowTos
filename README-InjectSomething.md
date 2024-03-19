# Inject Something

This is a section is working using the Spring framework only.

Injecting instance of classes works in a simple way: When the application starts, a special magic will be casted and create instances for any especially marks class members.

The package which are included while the application start could defined by setting the `@ComponentScan` annotation in the applications starter class or in a class annotated with `@Configuration`.

All classes which are marked with one of the annotations `@Component`, `@Configuration`, `@Named`, `@RestConroller` or `@Service` (I hope, not forgot someone) and placed in one of the configured packages will be included.

**NOTE:** Spring will use the singleton pattern for these instances.

There are different ways to inject one of the classes in instances of other classes which must be also annotated with one of the annotations as listed above.


## Depencendy Injection

By marking a class member with the annotation `@Inject` or `@Autowired`, a matching implementation of the class members type will be set to the specific class member.

In contrast to `@Inject`, `@Autowired` allows to configure an optional instantiation. If the `required` attribute is set to `false`, an instance will only be set, of there is an implementation found. Otherwise `null` is set as the class members value.

If the class member type is an interface, the spring magic will find a matching implementation for the class member. There should be one implementation marked with one of the listed annotations above only in the application.


## Constructor Injection

For `final` class members of classes which are marked with one of the listed annotations above, will also be set to an instance of a matching class implementation.

If the class member type is an interface, the spring magic will find a matching implementation for the class member. There should be one implementation marked with one of the listed annotations above only in the application.