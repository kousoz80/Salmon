cmake_minimum_required(VERSION 3.1)

add_library(UI STATIC MainWindow.cpp  ImageLabel.cpp TextLabel.cpp TweetContent.cpp TweetInfo.cpp ImageViewer.cpp VideoPlayer.cpp)
find_package(Phonon4Qt5 QUIET)
if(Phonon4Qt5_FOUND)
    target_link_libraries(UI Qt5::Widgets ${PHONON_LIBRARY}  Twitter)
    message( STATUS "Using Phonon4Qt5")
else(Phonon4Qt5_FOUND)
    find_package(Qt5 CONFIG REQUIRED Multimedia MultimediaWidgets)
    target_link_libraries(UI Qt5::Widgets Qt5::Multimedia Qt5::MultimediaWidgets Twitter)
    message( STATUS "Using Qt Multimedia")
endif(Phonon4Qt5_FOUND)
