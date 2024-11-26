CC=g++
LDFLAGS=-std=c++17
SOURCES=*.cpp
OBJECTS=$(SOURCES:.c=.o)
EXECUTABLE=CGR
INCLUDES=*.h

all: $(SOURCES) $(EXECUTABLE)
	
$(EXECUTABLE): $(OBJECTS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

%.o:  %.c  ${INCLUDES}
	$(CC) $(CFLAGS) $< -o $@

clean:
	rm $(EXECUTABLE)
	rm *.bmp 
	rm *.rpt 

