CXX = g++ -std=c++14
CXXFLAGS = -Wall -O -g -MMD # use -MMD to generate dependencies 
SOURCES = $(wildcard *.cpp)  # list of all .cc files in the current directory
OBJECTS = $(SOURCES:.cpp=.o) # .o files depend upon .cc files with same names
DEPENDS = ${OBJECTS:.o=.d}   # .d file is list of dependencies for corresponding .cc file
EXEC=main

# First target in the makefile is the default target.
# Note that the LIBFLAGS must come last in the command
$(EXEC): $(OBJECTS)
	$(CXX) $(CXXFLAGS) $(OBJECTS) -o $(EXEC)  $(LIBFLAGS)

%.o: %.cpp 
	$(CXX) -c -o $@ $< $(CXXFLAGS) $(LIBFLAGS)

-include ${DEPENDS}

.PHONY: clean
clean:
	rm  -f $(OBJECTS) $(DEPENDS) $(EXEC)
