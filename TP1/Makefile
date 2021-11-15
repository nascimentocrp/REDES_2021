CC := gcc 
CCFLAGS := -Wall -Wextra -fsanitize=address -fno-omit-frame-pointer -lpthread -lm
DBGFLAGS := -g
CCOBJFLAGS := $(CCFLAGS) -c 

CLIENT_TARGET := cliente
SERVER_TARGET := servidor

TARGET := $(CLIENT_TARGET) $(SERVER_TARGET)

COMMONOBJS = common.o

all:  $(TARGET)

runclient: $(CLIENT_TARGET)
	./$(CLIENT_TARGET) 127.0.0.1 5151

runserver: $(SERVER_TARGET)
	./$(SERVER_TARGET) v4 5151

runclient6: $(CLIENT_TARGET)
	./$(CLIENT_TARGET) ::1 5151

runserver6: $(SERVER_TARGET)
	./$(SERVER_TARGET) v6 5151

common.o: common.h common.c
	gcc $(CCOBJFLAGS) common.c

${CLIENT_TARGET}: $(COMMONOBJS)
	$(CC) $(CCFLAGS) client.c $(COMMONOBJS) -o $(CLIENT_TARGET)

${SERVER_TARGET}: $(COMMONOBJS)
	$(CC) $(CCFLAGS) server.c $(COMMONOBJS) -o $(SERVER_TARGET)

clean:
	$(RM) -rf *.o $(TARGET)

