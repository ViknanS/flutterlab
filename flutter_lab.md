# Flutter Laboratory – Experiments

**Name:** Viknan S
**Department:** Computer Science and Engineering

---

## Table of Contents

1. [Exp 1 – Student Profile (Basic Widgets)](#exp-1--student-profile-basic-widgets)
2. [Exp 2 – Responsive UI](#exp-2--responsive-ui)
3. [Exp 3 – Student Registration Form](#exp-3--student-registration-form)
4. [Exp 4 – Assets and Media (Images)](#exp-4--assets-and-media-images)
5. [Exp 5 – Navigation](#exp-5--navigation)
6. [Exp 6 – Animations and Transitions](#exp-6--animations-and-transitions)
7. [Exp 7 – State Management and JSON](#exp-7--state-management-and-json)
8. [Ollama Commands](#ollama-commands)
9. [Flutter Commands](#flutter-commands)

---

## Exp 1 – Student Profile (Basic Widgets)

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: const StudentProfile(),
    );
  }
}

class StudentProfile extends StatelessWidget {
  const StudentProfile({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Student Profile'),
      ),

      body: Column(
        children: [

          Container(
            padding: const EdgeInsets.all(20),
            child: const Column(
              children: [
                Text('Student Profile'),
                Text('Viknan S'),
                Text('Computer Science and Engineering'),
                Text('Flutter Laboratory'),
              ],
            ),
          ),

          Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: const [
              Icon(Icons.home),
              Icon(Icons.person),
              Icon(Icons.settings),
            ],
          ),

          Expanded(
            child: ListView(
              children: const [

                Card(
                  child: ListTile(
                    leading: Icon(Icons.book),
                    title: Text('Flutter'),
                    subtitle: Text('Mobile Application Development'),
                  ),
                ),

                ListTile(
                  leading: Icon(Icons.book),
                  title: Text('Flutter'),
                ),

                ListTile(
                  leading: Icon(Icons.cloud),
                  title: Text('Cloud Computing'),
                ),

                ListTile(
                  leading: Icon(Icons.code),
                  title: Text('Programming'),
                ),

              ],
            ),
          ),

        ],
      ),
    );
  }
}
```

---

## Exp 2 – Responsive UI

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: ResponsiveUI(),
    );
  }
}

class ResponsiveUI extends StatelessWidget {
  const ResponsiveUI({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Responsive UI'),
      ),

      body: LayoutBuilder(
        builder: (context, constraints) {

          if (constraints.maxWidth < 600) {

            // MOBILE LAYOUT
            return Column(
              children: const [
                Card(
                  child: ListTile(
                    leading: Icon(Icons.person),
                    title: Text('Student'),
                  ),
                ),

                Card(
                  child: ListTile(
                    leading: Icon(Icons.book),
                    title: Text('Courses'),
                  ),
                ),
              ],
            );

          } else {

            // DESKTOP LAYOUT
            return Row(
              children: const [
                Expanded(
                  child: Card(
                    child: ListTile(
                      leading: Icon(Icons.person),
                      title: Text('Student'),
                    ),
                  ),
                ),

                Expanded(
                  child: Card(
                    child: ListTile(
                      leading: Icon(Icons.book),
                      title: Text('Courses'),
                    ),
                  ),
                ),
              ],
            );
          }
        },
      ),
    );
  }
}
```

---

## Exp 3 – Student Registration Form

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: StudentForm(),
    );
  }
}

class StudentForm extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Student Registration Form'),
      ),

      body: Padding(
        padding: EdgeInsets.all(20),

        child: Column(
          children: [

            TextField(
              decoration: InputDecoration(
                labelText: 'Student Name',
                border: OutlineInputBorder(),
              ),
            ),

            SizedBox(height: 15),

            TextField(
              decoration: InputDecoration(
                labelText: 'Email',
                border: OutlineInputBorder(),
              ),
            ),

            SizedBox(height: 15),

            TextField(
              obscureText: true,
              decoration: InputDecoration(
                labelText: 'Password',
                border: OutlineInputBorder(),
              ),
            ),

            SizedBox(height: 20),

            ElevatedButton(
              onPressed: () {},
              child: Text('Submit'),
            ),

          ],
        ),
      ),
    );
  }
}
```

---

## Exp 4 – Assets and Media (Images)

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Assets and Media'),
        ),

        body: Column(
          children: [
            Text('Flutter Image Gallery'),

            Image.asset('assets/images/flutter.png'),

            Expanded(
              child: GridView.count(
                crossAxisCount: 2,
                children: [
                  Image.asset('assets/images/flutter.png'),
                  Image.asset('assets/images/flutter.png'),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

### `pubspec.yaml`

```yaml
flutter:
  assets:
    - assets/images/
```

> Place `flutter.png` inside `assets/images/` in the project root.

### Run

```bash
flutter pub get
flutter run
```

---

## Exp 5 – Navigation

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: HomePage(),
    );
  }
}

// HOME SCREEN
class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home'),
      ),

      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(
                builder: (context) => ProfilePage(),
              ),
            );
          },
          child: Text('Go to Profile'),
        ),
      ),
    );
  }
}

// PROFILE SCREEN
class ProfilePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Profile'),
      ),

      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [

            Text('Viknan S'),

            ElevatedButton(
              onPressed: () {
                Navigator.push(
                  context,
                  MaterialPageRoute(
                    builder: (context) => DetailsPage(),
                  ),
                );
              },
              child: Text('View Details'),
            ),

            ElevatedButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: Text('Back to Home'),
            ),

          ],
        ),
      ),
    );
  }
}

// DETAILS SCREEN
class DetailsPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Details'),
      ),

      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [

            Text('Details Screen'),

            Text('Course: Building Applications using Flutter'),

            ElevatedButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: Text('Back to Profile'),
            ),

          ],
        ),
      ),
    );
  }
}
```

---

## Exp 6 – Animations and Transitions

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: AnimationPage(),
    );
  }
}

class AnimationPage extends StatefulWidget {
  @override
  State<AnimationPage> createState() => _AnimationPageState();
}

class _AnimationPageState extends State<AnimationPage> {

  bool isLarge = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Animations and Transitions'),
      ),

      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [

            AnimatedContainer(
              duration: Duration(seconds: 1),
              width: isLarge ? 300 : 150,
              height: isLarge ? 300 : 150,
              decoration: BoxDecoration(
                color: Colors.blue,
                borderRadius: BorderRadius.circular(20),
              ),
              child: Center(
                child: Text('Flutter'),
              ),
            ),

            ElevatedButton(
              onPressed: () {
                setState(() {
                  isLarge = !isLarge;
                });
              },
              child: Text('Animate'),
            ),

          ],
        ),
      ),
    );
  }
}
```

---

## Exp 7 – State Management and JSON

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: StudentPage(),
    );
  }
}

class Student {
  int id;
  String name;
  String course;

  Student(this.id, this.name, this.course);

  Map<String, dynamic> toJson() {
    return {
      'id': id,
      'name': name,
      'course': course,
    };
  }

  factory Student.fromJson(Map<String, dynamic> json) {
    return Student(
      json['id'],
      json['name'],
      json['course'],
    );
  }
}

class StudentPage extends StatefulWidget {
  @override
  State<StudentPage> createState() => _StudentPageState();
}

class _StudentPageState extends State<StudentPage> {

  List<String> students = [];

  Student student = Student(1, 'Viknan S', 'CSE');

  @override
  Widget build(BuildContext context) {

    Map<String, dynamic> data = student.toJson();

    Student newStudent = Student.fromJson(data);

    return Scaffold(
      appBar: AppBar(
        title: Text('State Management and JSON'),
      ),

      body: Column(
        children: [

          Text('Object to JSON'),
          Text(data.toString()),

          Text('JSON to Object'),
          Text('Name: ${newStudent.name}'),

          ElevatedButton(
            onPressed: () {
              setState(() {
                students.add('Viknan S');
              });
            },
            child: Text('Add Student'),
          ),

          Text('Students added: ${students.length}'),

          Expanded(
            child: ListView.builder(
              itemCount: students.length,
              itemBuilder: (context, index) {
                return ListTile(
                  title: Text(students[index]),
                );
              },
            ),
          ),

        ],
      ),
    );
  }
}
```

---

## Ollama Commands

```bash
ollama --version
ollama serve
ollama list
ollama run llama3.2
/bye
```

---

## Flutter Commands

```bash
flutter create my_project
cd my_project
code .
flutter run -d chrome
```
