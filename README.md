# BookingRooms

The application is called RoomBooking

The app has three screens.
1.RoomsList Screen - List of rooms with limited info about the rooms.
2.Room Details Screen - It provides detailed information about the room like its capacity,equipments available,
Size etc and we can also view different images of the room by swiping the image with view indicator.
3.Add parcipant Screen - This is the final screen where the room can be booked by adding participants which in turn triggers
email to the intended participants about the meeting details.


I have used following components for the application

1.Retrofit for accessing webservice(A http library)
2.Picasso for dynamic Image loading and caching images
3.Gson for json parsing
4.Other UI components such as recyclerview,appcompat,v4 and v7 support libraries


Architecture Of RoomBooking Application

RoomBooking application follows MVP architecture i.e Model View Presenter.
There are three main modules that are present in the application

UI(or View)(For Example RoomListActivity)
Presenter(For Example RoomsPresenter)
Repository(RoomsRepository)

Ui & Presenter:
A Presenter provides the data for a specific UI component , such as a RoomsListActivity and handles the
communication with the business part of data handling, such as calling other components(namely RoomsRepository) to load the
data.I have followed package by feature approach for UI modules to easily segregate between screens(namely Home,AddParticipant,
Roomdetails)

RoomsRepository & model:
Presenter could have  directly called the 1aim Webservice to fetch the data and assign it back to the user object.
Even though it works, the  app will be difficult to maintain as it grows. It gives too much responsibility
to the Presenter class which goes against the principle of separation of concerns.Instead, our Presenter
will delegate this work to a new RoomsRepository module.RoomsRepository modules are responsible
for handling data operations. They provide a clean API to the rest of the app.It uses
retrofit to communicate to the server and parse the data into respective model objects.

The Room repository module can also  be extended to accommodate persisting data by following DAO pattern.

Other Supporting Modules or Packages:
api module : For Supporting Retrofit Module
model: contains all the POJO objects used in the application
util: contains validator api
