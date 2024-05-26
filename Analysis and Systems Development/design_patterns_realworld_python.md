### Creational Patterns

1. **Abstract Factory**

   **Example:** GUI Toolkit (e.g., creating Windows and Mac OS GUI elements)

   ```python
   class Button:
       def click(self):
           raise NotImplementedError()

   class WindowsButton(Button):
       def click(self):
           print("Windows Button clicked")

   class MacButton(Button):
       def click(self):
           print("Mac Button clicked")

   class GUIFactory:
       def create_button(self):
           raise NotImplementedError()

   class WindowsFactory(GUIFactory):
       def create_button(self):
           return WindowsButton()

   class MacFactory(GUIFactory):
       def create_button(self):
           return MacButton()

   def get_factory(os_type):
       if os_type == 'Windows':
           return WindowsFactory()
       elif os_type == 'Mac':
           return MacFactory()
       else:
           raise ValueError('Unknown OS type')

   factory = get_factory('Windows')
   button = factory.create_button()
   button.click()  # Output: Windows Button clicked
   ```

2. **Builder**

   **Example:** Building a complex object like a car with various parts

   ```python
   class Car:
       def __init__(self):
           self.wheels = None
           self.engine = None
           self.body = None

       def __str__(self):
           return f'Car with {self.wheels} wheels, {self.engine} engine, {self.body} body'

   class CarBuilder:
       def __init__(self):
           self.car = Car()

       def add_wheels(self, wheels):
           self.car.wheels = wheels
           return self

       def add_engine(self, engine):
           self.car.engine = engine
           return self

       def add_body(self, body):
           self.car.body = body
           return self

       def build(self):
           return self.car

   car = CarBuilder().add_wheels(4).add_engine('V8').add_body('SUV').build()
   print(car)  # Output: Car with 4 wheels, V8 engine, SUV body
   ```

3. **Factory Method**

   **Example:** Creating different types of documents

   ```python
   class Document:
       def display(self):
           raise NotImplementedError()

   class PDFDocument(Document):
       def display(self):
           print("Displaying PDF Document")

   class WordDocument(Document):
       def display(self):
           print("Displaying Word Document")

   class Application:
       def create_document(self, doc_type):
           if doc_type == 'PDF':
               return PDFDocument()
           elif doc_type == 'Word':
               return WordDocument()
           else:
               raise ValueError('Unknown document type')

   app = Application()
   doc = app.create_document('PDF')
   doc.display()  # Output: Displaying PDF Document
   ```

4. **Prototype**

   **Example:** Cloning objects, like game characters

   ```python
   import copy

   class GameCharacter:
       def __init__(self, name, level):
           self.name = name
           self.level = level

       def clone(self):
           return copy.deepcopy(self)

   character = GameCharacter('Elf', 10)
   cloned_character = character.clone()
   print(cloned_character.name, cloned_character.level)  # Output: Elf 10
   ```

5. **Singleton**

   **Example:** Database connection instance

   ```python
   class DatabaseConnection:
       _instance = None

       def __new__(cls):
           if cls._instance is None:
               cls._instance = super(DatabaseConnection, cls).__new__(cls)
           return cls._instance

   db1 = DatabaseConnection()
   db2 = DatabaseConnection()
   print(db1 is db2)  # Output: True
   ```

### Structural Patterns

1. **Adapter**

   **Example:** Adapting a third-party service interface to a required interface

   ```python
   class EuropeanSocket:
       def voltage(self):
           return 230

       def live(self):
           return 1

       def neutral(self):
           return -1

   class USASocket:
       def voltage(self):
           return 120

       def live(self):
           return 1

       def neutral(self):
           return -1

   class Adapter:
       def __init__(self, socket):
           self.socket = socket

       def voltage(self):
           return self.socket.voltage()

       def live(self):
           return self.socket.live()

       def neutral(self):
           return self.socket.neutral()

   european_socket = EuropeanSocket()
   adapter = Adapter(european_socket)
   print(adapter.voltage())  # Output: 230
   ```

2. **Bridge**

   **Example:** Separating the abstraction (remote control) from its implementation (TV)

   ```python
   class TV:
       def on(self):
           raise NotImplementedError()

       def off(self):
           raise NotImplementedError()

   class SonyTV(TV):
       def on(self):
           print("Sony TV is on")

       def off(self):
           print("Sony TV is off")

   class RemoteControl:
       def __init__(self, tv):
           self.tv = tv

       def turn_on(self):
           self.tv.on()

       def turn_off(self):
           self.tv.off()

   sony_tv = SonyTV()
   remote = RemoteControl(sony_tv)
   remote.turn_on()  # Output: Sony TV is on
   ```

3. **Composite**

   **Example:** Representing a file system hierarchy

   ```python
   class FileSystemComponent:
       def show_details(self):
           raise NotImplementedError()

   class File(FileSystemComponent):
       def __init__(self, name):
           self.name = name

       def show_details(self):
           print(f"File: {self.name}")

   class Directory(FileSystemComponent):
       def __init__(self, name):
           self.name = name
           self.children = []

       def add(self, component):
           self.children.append(component)

       def show_details(self):
           print(f"Directory: {self.name}")
           for child in self.children:
               child.show_details()

   file1 = File("file1.txt")
   file2 = File("file2.txt")
   directory = Directory("documents")
   directory.add(file1)
   directory.add(file2)
   directory.show_details()
   # Output:
   # Directory: documents
   # File: file1.txt
   # File: file2.txt
   ```

4. **Decorator**

   **Example:** Adding functionality to a simple text editor

   ```python
   class TextEditor:
       def display(self):
           raise NotImplementedError()

   class SimpleTextEditor(TextEditor):
       def display(self):
           return "Simple Text"

   class TextEditorDecorator(TextEditor):
       def __init__(self, editor):
           self.editor = editor

       def display(self):
           return self.editor.display()

   class BoldDecorator(TextEditorDecorator):
       def display(self):
           return f"<b>{self.editor.display()}</b>"

   editor = SimpleTextEditor()
   bold_editor = BoldDecorator(editor)
   print(bold_editor.display())  # Output: <b>Simple Text</b>
   ```

5. **Facade**

   **Example:** Simplifying access to a complex subsystem (e.g., home theater system)

   ```python
   class DVDPlayer:
       def on(self):
           print("DVD Player on")

       def play(self):
           print("DVD Player playing")

   class Amplifier:
       def on(self):
           print("Amplifier on")

       def set_volume(self, level):
           print(f"Amplifier volume set to {level}")

   class HomeTheaterFacade:
       def __init__(self, dvd_player, amplifier):
           self.dvd_player = dvd_player
           self.amplifier = amplifier

       def watch_movie(self):
           self.dvd_player.on()
           self.amplifier.on()
           self.amplifier.set_volume(5)
           self.dvd_player.play()

   dvd_player = DVDPlayer()
   amplifier = Amplifier()
   home_theater = HomeTheaterFacade(dvd_player, amplifier)
   home_theater.watch_movie()
   # Output:
   # DVD Player on
   # Amplifier on
   # Amplifier volume set to 5
   # DVD Player playing
   ```

6. **Flyweight**

   **Example:** Managing a large number of similar objects (e.g., characters in a text editor)

   ```python
   class Character:
       _instances = {}

       def __new__(cls, char):
           if char not in cls._instances:
               cls._instances[char] = super(Character, cls).__new__(cls)
               cls._instances[char].char = char
           return cls._instances[char]

       def display(self, font, size):
           print(f"Character: {self.char}, Font: {font}, Size: {size}")

   c1 = Character('a')
   c2 = Character('a')
   print(c1 is c2)  # Output: True
   c1.display('Arial', 12)
   # Output: Character: a, Font: Arial, Size: 12
   ```

7. **Proxy**

   **Example:** Providing controlled access to an expensive object (e.g., a large image file)

   ```python
   class Image:
       def display(self):
           raise NotImplementedError()

   class RealImage(Image):
       def __init__(self, filename):
           self.filename = filename
           self.load_image()

       def load_image(self):
           print(f"Loading image from {self.filename}")

       def display(self):
           print(f"Displaying {self.filename}")

   class ProxyImage(Image):
       def __init__(self, filename):
           self.filename = filename
           self.real_image = None

       def display(self):
           if self.real_image is None:
               self.real_image = RealImage(self.filename)
           self.real_image.display()

   image = ProxyImage("large_image.jpg")
   image.display()
   # Output:
   # Loading image from large_image.jpg
   # Displaying large_image.jpg
   ```

### Behavioral Patterns

1. **Chain of Responsibility**

   **Example:** Handling a sequence of requests in a support system

   ```python
   class SupportHandler:
       def __init__(self, successor=None):
           self.successor = successor

       def handle(self, request):
           raise NotImplementedError()

   class BasicSupportHandler(SupportHandler):
       def handle(self, request):
           if request == 'basic':
               print("Basic support handled")
           elif self.successor:
               self.successor.handle(request)

   class AdvancedSupportHandler(SupportHandler):
       def handle(self, request):
           if request == 'advanced':
               print("Advanced support handled")
           elif self.successor:
               self.successor.handle(request)

   handler = BasicSupportHandler(AdvancedSupportHandler())
   handler.handle('advanced')  # Output: Advanced support handled
   ```

2. **Command**

   **Example:** Implementing an undo feature in a text editor

   ```python
   class Command:
       def execute(self):
           raise NotImplementedError()

       def undo(self):
           raise NotImplementedError()

   class TextEditor:
       def __init__(self):
           self.text = ""

       def append_text(self, text):
           self.text += text

       def delete_text(self, length):
           self.text = self.text[:-length]

   class AppendCommand(Command):
       def __init__(self, editor, text):
           self.editor = editor
           self.text = text

       def execute(self):
           self.editor.append_text(self.text)

       def undo(self):
           self.editor.delete_text(len(self.text))

   editor = TextEditor()
   command = AppendCommand(editor, "Hello")
   command.execute()
   print(editor.text)  # Output: Hello
   command.undo()
   print(editor.text)  # Output: 
   ```

3. **Interpreter**

   **Example:** Evaluating mathematical expressions

   ```python
   class Expression:
       def interpret(self, context):
           raise NotImplementedError()

   class Number(Expression):
       def __init__(self, number):
           self.number = number

       def interpret(self, context):
           return self.number

   class Add(Expression):
       def __init__(self, left, right):
           self.left = left
           self.right = right

       def interpret(self, context):
           return self.left.interpret(context) + self.right.interpret(context)

   context = {}
   expression = Add(Number(1), Number(2))
   result = expression.interpret(context)
   print(result)  # Output: 3
   ```

4. **Iterator**

   **Example:** Iterating over a collection of items

   ```python
   class Iterator:
       def __init__(self, collection):
           self.collection = collection
           self.index = 0

       def __iter__(self):
           return self

       def __next__(self):
           if self.index < len(self.collection):
               result = self.collection[self.index]
               self.index += 1
               return result
           else:
               raise StopIteration

   collection = [1, 2, 3, 4]
   iterator = Iterator(collection)
   for item in iterator:
       print(item)
   # Output: 1 2 3 4
   ```

5. **Mediator**

   **Example:** Coordinating communication between different components in a chat room

   ```python
   class ChatRoom:
       def show_message(self, user, message):
           print(f"[{user}]: {message}")

   class User:
       def __init__(self, name, chatroom):
           self.name = name
           self.chatroom = chatroom

       def send_message(self, message):
           self.chatroom.show_message(self.name, message)

   chatroom = ChatRoom()
   user1 = User("Alice", chatroom)
   user2 = User("Bob", chatroom)
   user1.send_message("Hello, Bob!")
   user2.send_message("Hello, Alice!")
   # Output:
   # [Alice]: Hello, Bob!
   # [Bob]: Hello, Alice!
   ```

6. **Memento**

   **Example:** Saving and restoring the state of an object (e.g., game save)

   ```python
   class Memento:
       def __init__(self, state):
           self.state = state

   class Game:
       def __init__(self):
           self.state = "Start"

       def play(self):
           self.state = "Playing"

       def save(self):
           return Memento(self.state)

       def restore(self, memento):
           self.state = memento.state

   game = Game()
   game.play()
   memento = game.save()
   game.state = "Game Over"
   game.restore(memento)
   print(game.state)  # Output: Playing
   ```

7. **Observer**

   **Example:** Implementing a subscription mechanism for stock price updates

   ```python
   class Stock:
       def __init__(self):
           self.observers = []
           self._price = 0

       def subscribe(self, observer):
           self.observers.append(observer)

       def unsubscribe(self, observer):
           self.observers.remove(observer)

       @property
       def price(self):
           return self._price

       @price.setter
       def price(self, value):
           self._price = value
           self.notify()

       def notify(self):
           for observer in self.observers:
               observer.update(self)

   class Investor:
       def update(self, stock):
           print(f"Stock price updated to {stock.price}")

   stock = Stock()
   investor = Investor()
   stock.subscribe(investor)
   stock.price = 100  # Output: Stock price updated to 100
   ```

8. **State**

   **Example:** Managing the state of a TCP connection

   ```python
   class TCPState:
       def open(self, connection):
           raise NotImplementedError()

       def close(self, connection):
           raise NotImplementedError()

       def acknowledge(self, connection):
           raise NotImplementedError()

   class TCPOpenState(TCPState):
       def open(self, connection):
           print("TCP connection is already open")

       def close(self, connection):
           print("Closing TCP connection")
           connection.state = TCPClosedState()

       def acknowledge(self, connection):
           print("Acknowledging TCP connection")

   class TCPClosedState(TCPState):
       def open(self, connection):
           print("Opening TCP connection")
           connection.state = TCPOpenState()

       def close(self, connection):
           print("TCP connection is already closed")

       def acknowledge(self, connection):
           print("Cannot acknowledge, TCP connection is closed")

   class TCPConnection:
       def __init__(self):
           self.state = TCPClosedState()

       def open(self):
           self.state.open(self)

       def close(self):
           self.state.close(self)

       def acknowledge(self):
           self.state.acknowledge(self)

   connection = TCPConnection()
   connection.open()        # Output: Opening TCP connection
   connection.acknowledge() # Output: Acknowledging TCP connection
   connection.close()       # Output: Closing TCP connection
   ```

9. **Strategy**

   **Example:** Implementing different sorting algorithms

   ```python
   class SortStrategy:
       def sort(self, data):
           raise NotImplementedError()

   class QuickSort(SortStrategy):
       def sort(self, data):
           print("QuickSort algorithm")
           return sorted(data)  # Placeholder for actual QuickSort implementation

   class MergeSort(SortStrategy):
       def sort(self, data):
           print("MergeSort algorithm")
           return sorted(data)  # Placeholder for actual MergeSort implementation

   class Sorter:
       def __init__(self, strategy):
           self.strategy = strategy

       def sort(self, data):
           return self.strategy.sort(data)

   data = [5, 2, 9, 1]
   sorter = Sorter(QuickSort())
   sorter.sort(data)  # Output: QuickSort algorithm
   ```

10. **Template Method**

    **Example:** Defining a skeleton algorithm for data processing

    ```python
    class DataProcessor:
        def process(self):
            self.read_data()
            self.process_data()
            self.save_data()

        def read_data(self):
            raise NotImplementedError()

        def process_data(self):
            raise NotImplementedError()

        def save_data(self):
            print("Saving data")

    class CSVDataProcessor(DataProcessor):
        def read_data(self):
            print("Reading CSV data")

        def process_data(self):
            print("Processing CSV data")

    processor = CSVDataProcessor()
    processor.process()
    # Output:
    # Reading CSV data
    # Processing CSV data
    # Saving data
    ```

11. **Visitor**

    **Example:** Performing operations on elements of an object structure (e.g., a document)

    ```python
    class DocumentElement:
        def accept(self, visitor):
            raise NotImplementedError()

    class Paragraph(DocumentElement):
        def accept(self, visitor):
            visitor.visit_paragraph(self)

    class Image(DocumentElement):
        def accept(self, visitor):
            visitor.visit_image(self)

    class DocumentVisitor:
        def visit_paragraph(self, paragraph):
            raise NotImplementedError()

        def visit_image(self, image):
            raise NotImplementedError()



    class RenderVisitor(DocumentVisitor):
        def visit_paragraph(self, paragraph):
            print("Rendering paragraph")

        def visit_image(self, image):
            print("Rendering image")

    document = [Paragraph(), Image()]
    visitor = RenderVisitor()
    for element in document:
        element.accept(visitor)
    # Output:
    # Rendering paragraph
    # Rendering image
    ```

These examples demonstrate how GOF design patterns can be implemented and used in Python to solve common software design problems.
