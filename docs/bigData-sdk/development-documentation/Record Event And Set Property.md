### Record Event And Set Property

<br>

#### Set User Info

You can set user info by instance:

```
instance->SetUserInfo(userName);
```

Currently only a simple name can be set to distinguish between different users, of course, this is not necessary.

If you set the user information, each event and property will be stored with the user information together.

#### Record Event

You can record event by instance:

```
instance->RecordEvent(eventName, eventHandler, timestamp);
```

You can customize the name of the event, but do not conflict with the reserved word. If success, it will return HybSuccess, otherwise return an error code. Please query the error code table to determine what is wrong.

After the record success, it will output a number as a handle, if you set a property that it associated with this event, you need to use the handle as a param.

The timestamp can be determined by you, fill in 0 or do not fill it will use the current system time as a timestamp.

#### Set Property

You can set property by instance:

```
instance->SetEventProperty(eventName, eventHandler, propertyName, propertyValue);
```

or

```
PropertyType propertyVal;
PropertyFunction {
public:
	template<typename T>
	static const char * toString(T val);
}
instance->SetEventProperty<PropertyType, PropertyFunction>(eventName, eventHandler, propertyName, propertyValue);
```

By default, several basic data types are supported, such as int, double, float, unsigned int and string.

If you need to record complex data types or custom data types, please provide a method(PropertyFunction::toString) that can convert it into a string.
