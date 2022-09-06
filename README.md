
# Opportunity with Tata Digital - Flutter Test

Please find the Questions and Answeres below


#### 1) What is the difference between Hot Reload and Hot Restart?

Hot reload feature quickly compile the newly added code in our file and sent the code to Dart Virtual Machine. After done updating the Code Dart Virtual Machine update the app UI with widgets.

In Hot restart, it destroys the preserves State value and set them to their default. So if you are using state value in your application then after every hot restart the developer gets fully compiled application and all the states will be set to their defaults.

#### 2) What are the different ways we can create a custom widget?

We create Custom Widgets when we want a custom look and feel to our app, and we know that there will be a repetition of a particular widget. We can create the custom widget in a new dart file with all the codes and defining the parameters that we need in the constructor.

#### 3) How can I access platform(iOS or Android) specific code from Flutter?

Using  MethodChannel we can access platform(iOS or Android) specific code from Flutter

for that we need to do following spets
    - Create the Flutter platform client
    - Add an Android/iOS  platform-specific implementation

#### 4)  What do you know about eventloop and what is the relationship with isolates?

An isolate is what all Dart code runs in. It's like a little space on the machine with its own private chunk of memory and a single thread running an event loop.

In Dart, though, each thread is in its own isolate with its own memory and it just processes events.

Many Dart apps run all their code in a single isolate, but you can have more than one if you need it.

If you have a computation to perform that's so enormous it could cause you to drop frames if it were run in the main isolate, you can use Isolate.spawn() or Flutter's compute function, both of which create a separate

isolate to do the number crunching, leaving your main one free to rebuild and render the widget tree in the meantime.

That new isolate will get its own event loop and its own memory, which the original isolate, even though it's the parent of this new one, isn't allowed to access.

That's the source of the name isolate.

These little spaces are kept isolated from one another.

In fact, the only way they can work together is by passing messages back and forth.

One isolate will send a message to the other, and that receiving isolate process is the message using its event loop.
## Coding Questions And Answers:

#### 1) Refactor the code below so that the children will wrap to the next line when the display width is small for them to fit.

```Dart

class MyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Wrap(
      children: const [
         Chip(label: Text("I")),
         Chip(label: Text("am")),
         Chip(label: Text("looking")),
         Chip(label: Text("for")),
         Chip(label: Text("a")),
         Chip(label: Text("job")),
         Chip(label: Text("and")),
         Chip(label: Text("I")),
         Chip(label: Text("need")),
         Chip(label: Text("a")),
         Chip(label: Text("job")),
      ],
    );
  }
}
```

## Screenshots

![App Screenshot](https://github.com/hthakore/TATA-DIGITAL-TEST/blob/main/que_1_1.png)

![App Screenshot](https://github.com/hthakore/TATA-DIGITAL-TEST/blob/main/que_1_short.png)

#### 2) Write a function to call the below mentioned API and parse the data. Make sure the function return an object of News item, which contains News article Title, News article Content, Date of News Published, Banner Image of News article. https://inshorts.deta.dev/news?category=all


#### News Model Class
```Dart
class News {
  String? _category;
  List<Data>? _data;
  bool? _success;

  News({String? category, List<Data>? data, bool? success}) {
    if (category != null) {
      this._category = category;
    }
    if (data != null) {
      this._data = data;
    }
    if (success != null) {
      this._success = success;
    }
  }

  String? get category => _category;
  set category(String? category) => _category = category;
  List<Data>? get data => _data;
  set data(List<Data>? data) => _data = data;
  bool? get success => _success;
  set success(bool? success) => _success = success;

  News.fromJson(Map<String, dynamic> json) {
    _category = json['category'];
    if (json['data'] != null) {
      _data = <Data>[];
      json['data'].forEach((v) {
        _data!.add(new Data.fromJson(v));
      });
    }
    _success = json['success'];
  }

  Map<String, dynamic> toJson() {
    final Map<String, dynamic> data = new Map<String, dynamic>();
    data['category'] = this._category;
    if (this._data != null) {
      data['data'] = this._data!.map((v) => v.toJson()).toList();
    }
    data['success'] = this._success;
    return data;
  }
}

class Data {
  String? _author;
  String? _content;
  String? _date;
  String? _id;
  String? _imageUrl;
  String? _readMoreUrl;
  String? _time;
  String? _title;
  String? _url;

  Data(
      {String? author,
      String? content,
      String? date,
      String? id,
      String? imageUrl,
      String? readMoreUrl,
      String? time,
      String? title,
      String? url}) {
    if (author != null) {
      this._author = author;
    }
    if (content != null) {
      this._content = content;
    }
    if (date != null) {
      this._date = date;
    }
    if (id != null) {
      this._id = id;
    }
    if (imageUrl != null) {
      this._imageUrl = imageUrl;
    }
    if (readMoreUrl != null) {
      this._readMoreUrl = readMoreUrl;
    }
    if (time != null) {
      this._time = time;
    }
    if (title != null) {
      this._title = title;
    }
    if (url != null) {
      this._url = url;
    }
  }

  String? get author => _author;
  set author(String? author) => _author = author;
  String? get content => _content;
  set content(String? content) => _content = content;
  String? get date => _date;
  set date(String? date) => _date = date;
  String? get id => _id;
  set id(String? id) => _id = id;
  String? get imageUrl => _imageUrl;
  set imageUrl(String? imageUrl) => _imageUrl = imageUrl;
  String? get readMoreUrl => _readMoreUrl;
  set readMoreUrl(String? readMoreUrl) => _readMoreUrl = readMoreUrl;
  String? get time => _time;
  set time(String? time) => _time = time;
  String? get title => _title;
  set title(String? title) => _title = title;
  String? get url => _url;
  set url(String? url) => _url = url;

  Data.fromJson(Map<String, dynamic> json) {
    _author = json['author'];
    _content = json['content'];
    _date = json['date'];
    _id = json['id'];
    _imageUrl = json['imageUrl'];
    _readMoreUrl = json['readMoreUrl'];
    _time = json['time'];
    _title = json['title'];
    _url = json['url'];
  }

  Map<String, dynamic> toJson() {
    final Map<String, dynamic> data = new Map<String, dynamic>();
    data['author'] = this._author;
    data['content'] = this._content;
    data['date'] = this._date;
    data['id'] = this._id;
    data['imageUrl'] = this._imageUrl;
    data['readMoreUrl'] = this._readMoreUrl;
    data['time'] = this._time;
    data['title'] = this._title;
    data['url'] = this._url;
    return data;
  }
}

News newsFromJson(String str) => News.fromJson(json.decode(str));

String newsdataToJson(News data) => json.encode(News.toJson());

```

#### Method that call URL and Return News
```Dart
Future<List<Data>> getNews() async{
  final response = await http.get('https://inshorts.deta.dev/news?category=all');
  if (response.statusCode == 200) {
    final news = newsFromJson(response.body)
    return news.data
  }
  return [];
}
```

#### 3) Identify the problem in the following code block and correct it.

#### Added async and Future to method
```Dart
Future<String> longRunningOperation() async {
  var counting = 0;
  for (var i = 1; i < 1000000000; i ++) {
    counting = i;
  }
  return "$counting!, times I print value!";
}
```
