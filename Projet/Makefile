NAME := FoxWar

SRC_DIR := src
INCLUDE_DIR := include
BUILD_DIR := _build

CXX ?= c++
CPPFLAGS ?= -std=c++11 -Wall -g -O3 

INCLUDE := -I$(INCLUDE_DIR)

EXEC := $(NAME).exe

all: build clean

clean:
	rm -rf $(BUILD_DIR)
	
mrproper: clean
	rm -f $(EXEC)

HPP_FILES := $(wildcard $(INCLUDE_DIR)/*.hpp)
CPP_FILES := $(HPP_FILES:$(INCLUDE_DIR)/%.hpp=$(SRC_DIR)/%.cpp)
O_FILES := $(CPP_FILES:$(SRC_DIR)/%.cpp=$(BUILD_DIR)/%.o)

default: build

build: $(EXEC)

$(BUILD_DIR):
	mkdir -p $@

$(BUILD_DIR)/%.o: $(SRC_DIR)/%.cpp $(INCLUDE_DIR)/%.hpp
	$(CXX) -o $@ -c $< $(CPPFLAGS) $(INCLUDE)

$(EXEC): $(BUILD_DIR) $(O_FILES)
	$(CXX) -o $@ $(O_FILES)
	

.PHONY: clean mrproper
