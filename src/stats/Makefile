UTILITIES_DIR = ../common/
OBJ_DIR = ../../obj/
BIN_DIR = ../../bin/


# -------------------
# define our includes
# -------------------
INCLUDES = -I$(UTILITIES_DIR)/tabFile/ -I$(UTILITIES_DIR)/lineFileUtilities/ -I$(UTILITIES_DIR)/version/ -I$(UTILITIES_DIR)/gzstream/ -I$(UTILITIES_DIR)/fileType/

# ----------------------------------
# define our source and object files
# ----------------------------------
SOURCES= stats.cpp
OBJECTS= $(SOURCES:.cpp=.o)
_EXT_OBJECTS=tabFile.o gzstream.o fileType.o
EXT_OBJECTS=$(patsubst %,$(OBJ_DIR)/%,$(_EXT_OBJECTS))
BUILT_OBJECTS= $(patsubst %,$(OBJ_DIR)/%,$(OBJECTS))
PROGRAM= stats


all: $(PROGRAM)

.PHONY: all


$(PROGRAM): $(BUILT_OBJECTS) $(EXT_OBJECTS)
	@echo "  * linking $(PROGRAM)"
	@$(CXX) $(LDFLAGS) $(CXXFLAGS) -o $(BIN_DIR)/$@ $^ $(LIBS)

$(BUILT_OBJECTS): $(SOURCES)
	@echo "  * compiling" $(*F).cpp
	@$(CXX) -c -o $@ $(*F).cpp $(LDFLAGS) $(CXXFLAGS) $(INCLUDES)

$(EXT_OBJECTS):
	@$(MAKE) --no-print-directory -C $(UTILITIES_DIR)/tabFile/
	@$(MAKE) --no-print-directory -C $(UTILITIES_DIR)/gzstream/
	@$(MAKE) --no-print-directory -C $(UTILITIES_DIR)/fileType/	
	
clean:
	@echo "Cleaning up."
	@rm -f $(OBJ_DIR)/* $(BIN_DIR)/*

.PHONY: clean