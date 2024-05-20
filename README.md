# Flutter Chat App

This is a simple chat application built with Flutter, which allows users to log in, send text messages, and share images in a chat conversation.

## Features

- User authentication (login/logout)
- Real-time messaging
- Image sharing
- Responsive UI for different screen sizes

## Getting Started

To run this project locally, follow these steps:

1. Make sure you have Flutter installed on your machine. You can follow the official Flutter installation guide [here](https://flutter.dev/docs/get-started/install).

2. Clone this repository: `git clone https://github.com/your-username/flutter-chat-app.git`

3. Navigate to the project directory: `cd flutter-chat-app`

4. Get the required packages: `flutter pub get`

5. Run the app on your preferred device or emulator: `flutter run`

## Dependencies

This project uses the following third-party packages:

- [provider](https://pub.dev/packages/provider) - State management
- [shared_preferences](https://pub.dev/packages/shared_preferences) - Persistent data storage
- [http](https://pub.dev/packages/http) - Making HTTP requests
- [json_annotation](https://pub.dev/packages/json_annotation) - JSON (de)serialization
- [social_media_buttons](https://pub.dev/packages/social_media_buttons) - Rendering social media buttons
- [url_launcher](https://pub.dev/packages/url_launcher) - Launching URLs
- [google_fonts](https://pub.dev/packages/google_fonts) - Using Google Fonts

## Project Structure

```
flutter-chat-app
├── chat_app
│   ├── android
│   ├── assets
│   ├── ios
│   ├── lib
│   │   ├── demo
│   │   ├── models
│   │   ├── repo
│   │   ├── services
│   │   ├── utils
│   │   ├── widgets
│   │   └── ...
│   ├── macos
│   ├── test
│   ├── web
│   └── ...
├── resources
└── ...
```

- `chat_app/lib`: Contains the main application code, including pages, models, services, utilities, and widgets.
- `chat_app/assets`: Holds static assets like images and JSON files.
- Other directories are related to the Flutter project structure.

## High-Level System Architecture Diagram

here's a high-level PlantUML diagram representing the system architecture of the Flutter chat app:

![High-Level System Architecture Diagram](https://github.com/majekolaitan/flutter-chat-app/blob/main/resources/diagram-system-architecture.png)

This diagram illustrates the high-level components of the Flutter chat app and their relationships. The main components are:

1. **Flutter App**: The main entry point of the Flutter application.
2. **Flutter Pages**: Contains the main pages of the app, such as `ChatPage` and `LoginPage`.
3. **Flutter Widgets**: Contains reusable UI components like `ChatBubble`, `ChatInput`, `LoginTextField`, and `PickerBody`.
4. **Flutter Models**: Contains data models like `ChatMessageEntity` and `ImageModel`.
5. **Flutter Services**: Contains services like `AuthService` for authentication and user management.
6. **Flutter Repositories**: Contains repositories like `ImageRepository` for fetching data from APIs.
7. **Flutter Utils**: Contains utility classes for colors, spacing, and text field styles.

The diagram shows the dependencies and relationships between these components. For example, the `Flutter Pages` and `Flutter Widgets` components depend on the `Flutter Models`, `Flutter Services`, and other utility components.

Note that this is a high-level representation, and the actual implementation may have additional components or dependencies not shown in this diagram.

## UML Use Case Diagram

Here's a UML use case diagram representing the main use cases and actors in the Flutter chat app:

![UML Use Case Diagram](https://github.com/majekolaitan/flutter-chat-app/blob/main/resources/diagram-uml-use-case.png)

This use case diagram illustrates the main actors and use cases in the Flutter chat app. Here's a breakdown of the elements:

1. **Actor**: `User` represents the end-user who interacts with the chat application.

2. **Use Cases**:
   - `Login`: Allows the user to authenticate and log into the chat application.
   - `View Chat History`: Displays the chat history, including previously sent messages and images.
   - `Send Message`: Enables the user to type and send text messages.
   - `Attach Image`: Allows the user to attach and send images along with text messages.
   - `Logout`: Provides the functionality for the user to log out of the chat application.

The diagram shows the relationships between the use cases and the actor:

- The `User` directly interacts with the `Login` use case.
- The `View Chat History` use case includes the `Send Message` and `Logout` use cases, indicating that the user can perform these actions while viewing the chat history.
- The `Send Message` use case includes the `Attach Image` use case, enabling the user to attach images while sending messages.

This use case diagram provides a high-level overview of the main functionalities of the chat application from the user's perspective. It helps in understanding the scope of the application and the interactions between the user and the system.

Note that this diagram does not cover all the details of the application's functionality or any specific implementation details. It serves as a conceptual representation of the primary use cases and their relationships.

## UML Activity Diagram

Here's a UML activity diagram representing the user authentication and chat flow in the Flutter chat app:

![UML Activity Diagram](https://github.com/majekolaitan/flutter-chat-app/blob/main/resources/diagram-uml-activity.png)

This activity diagram illustrates the flow of user authentication and chat functionality in the Flutter chat app. Here's a breakdown of the activities:

1. The app checks if the user is already logged in by checking the `SharedPreferences`.
2. If the user is logged in, the app navigates to the `ChatPage`.
3. If the user is not logged in, the app navigates to the `LoginPage`.
4. On the `LoginPage`, the user enters their username and password.
5. The app validates the form fields.
6. If the form is valid, the app logs in the user, stores the username in `SharedPreferences`, and navigates to the `ChatPage`.
7. If the form is invalid, the app displays an error message.
8. On the `ChatPage`, the user can perform the following actions:
   - Send a message: The user types a message, optionally adds an image, and sends the message. The chat history is updated.
   - Log out: The user logs out, the `SharedPreferences` are cleared, and the app navigates back to the `LoginPage`.

This diagram provides a high-level overview of the user authentication and chat flow in the app, including the decision points, actions, and transitions between different states.

Note that this diagram focuses on the main flow and does not cover all possible scenarios or edge cases that may be present in the actual implementation.

...

## Folder Structure and Relationships

Let's go through the different files and understand their purpose, properties, methods, and relationships.

1. **Folder Structure**:

   - The `chat_app` folder contains the main Flutter application code.
   - The `lib` folder holds the Dart code for the application.
   - The `models` folder contains data models like `chat_message_entity.dart` and `image_model.dart`.
   - The `repo` folder has a repository class `image_repository.dart` to fetch images from an API.
   - The `services` folder contains the `auth_service.dart` for handling user authentication.
   - The `utils` folder has utility classes for colors, spacing, and text field styles.
   - The `widgets` folder contains reusable widgets like `chat_bubble.dart`, `chat_input.dart`, `login_text_field.dart`, and `picker_body.dart`.
   - The main files are `chat_page.dart`, `login_page.dart`, and `main.dart`.

2. **chat_page.dart**:

   - `ChatPage` is a `StatefulWidget` that displays the chat screen.
   - It loads initial mock messages from a JSON file using `_loadInitialMessages()`.
   - The `build` method constructs the UI with an `AppBar`, a `ListView` to display chat messages, and a `ChatInput` widget.
   - The `onMessageSent` method adds a new chat message to the `_messages` list and updates the UI.

3. **chat_message_entity.dart**:

   - `ChatMessageEntity` is a data model class representing a chat message.
   - It has properties like `text`, `imageUrl`, `id`, `createdAt`, and `author` (an `Author` object).
   - The `Author` class represents the author of a chat message with a `userName` property.

4. **image_model.dart**:

   - `PixelfordImage` is a data model class representing an image fetched from the Pixelford API.
   - It has properties like `id`, `filename`, `title`, `urlFullSize`, and `urlSmallSize`.
   - The `fromJson` and `toJson` methods are used for JSON serialization and deserialization.

5. **image_repository.dart**:

   - `ImageRepository` is a class that fetches images from the Pixelford API using an HTTP GET request.
   - The `getNetworkImages` method returns a list of `PixelfordImage` objects.
   - It handles various exceptions like `SocketException`, `HttpException`, and `FormatException`.

6. **auth_service.dart**:

   - `AuthService` is a `ChangeNotifier` class that handles user authentication.
   - It uses `SharedPreferences` to store and retrieve the user's name.
   - It provides methods like `loginUser`, `isLoggedIn`, `logoutUser`, `getUserName`, and `updateUserName`.

7. **login_page.dart**:

   - `LoginPage` is a `StatelessWidget` that displays the login screen.
   - It has a form with text fields for username and password, and a login button.
   - The `loginUser` method validates the form and logs in the user using the `AuthService`.
   - It also displays some additional information and links.

8. **main.dart**:

   - This is the entry point of the Flutter application.
   - It initializes the `AuthService` and provides it to the application using a `ChangeNotifierProvider`.
   - The `ChatApp` widget sets up the `MaterialApp` and handles the initial route based on the user's login status.

9. **chat_bubble.dart**:

   - `ChatBubble` is a stateless widget that displays a single chat message bubble.
   - It takes a `ChatMessageEntity` object and an `Alignment` as input.
   - The widget displays the message text and an optional image if present.
   - The bubble's color and alignment depend on whether the message is from the current user or not.

10. **chat_input.dart**:

    - `ChatInput` is a `StatefulWidget` that allows the user to input new chat messages.
    - It has a text field for typing messages and buttons for sending messages and picking images.
    - The `onSendButtonPressed` method creates a new `ChatMessageEntity` object and calls the `onSubmit` callback with it.
    - The `onImagePicked` method updates the selected image URL and closes the image picker bottom sheet.

11. **login_text_field.dart**:

    - `LoginTextField` is a stateless widget that represents a text field for the login form.
    - It takes properties like `controller`, `hintText`, `validator`, and `hasAsterisks` (for password fields).

12. **picker_body.dart**:
    - `NetworkImagePickerBody` is a stateless widget that displays a grid of images fetched from the Pixelford API.
    - It uses the `ImageRepository` class to fetch the images.
    - When an image is tapped, the `onImageSelected` callback is called with the selected image URL.

The main flow of the application is as follows:

1. The `main.dart` file initializes the `AuthService` and creates the `MaterialApp`.
2. If the user is logged in, the `ChatPage` is displayed; otherwise, the `LoginPage` is shown.
3. On the `LoginPage`, the user enters their username and password, and the `loginUser` method is called to authenticate the user.
4. After successful authentication, the `ChatPage` is displayed, showing the initial mock messages.
5. The user can type a new message in the `ChatInput` widget and send it by clicking the send button or picking an image from the image picker.
6. New messages are added to the `_messages` list and displayed in the `ListView`.
7. The user can log out by clicking the logout button in the `AppBar`.

The application uses various Flutter concepts like `StatefulWidget`, `ChangeNotifier`, `FutureBuilder`, `GridView`, and more. It also incorporates external libraries like `provider`, `shared_preferences`, `http`, and `json_annotation` for state management, local storage, HTTP requests, and JSON serialization/deserialization, respectively.

## UML Class Diagram

Here's the PlantUML code for the class diagram of the chat application:

![UML Class Diagram](https://github.com/majekolaitan/flutter-chat-app/blob/main/resources/diagram-uml-class.png)

This PlantUML code defines the classes and their relationships in the chat application. The classes are represented by boxes with their respective properties and methods. The relationships between classes are shown using different types of arrows:

- `*--` represents composition (strong ownership)
- `o--` represents aggregation (weak ownership)
- `..>` represents dependency or association

The diagram shows how the main classes like `ChatPage`, `LoginPage`, `ChatMessageEntity`, `PixelfordImage`, `AuthService`, and `ImageRepository` are related to each other and to the supporting classes like `ChatBubble`, `ChatInput`, `LoginTextField`, and `NetworkImagePickerBody`.
