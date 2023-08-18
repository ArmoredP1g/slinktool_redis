
# Build environment can be configured the following
# environment variables:
#   CC : Specify the C compiler to use
#   CFLAGS : Specify compiler options to use

# Required compiler parameters
# 定义了一个名为 CFLAGS 的变量，用于指定编译选项。这里的选项是 -I，用于指定头文件的搜索路径。
CFLAGS += -I../libslink -I../ezxml


# 定义了两个变量，LDFLAGS 和 LDLIBS，用于指定连接器选项和链接库
LDFLAGS = -L../libslink -L../ezxml
LDLIBS  = -lslink -lezxml

# For Windows w/ Unix-like build environments uncomment the following line
# This is needed for MinGW but not for Cygwin
# 如果在 Windows 平台上使用类 Unix 的构建环境，则需要将上面的变量改为以下内容。这是 MinGW 所必需的，但对于 Cygwin 则不需要。
#LDLIBS = -lslink -lezxml -lws2_32

# For SunOS/Solaris uncomment the following line
#LDLIBS = -lslink -lezxml -lsocket -lnsl -lrt


# 定义了一个名为 BIN 的变量，用于指定最终生成的二进制文件的路径和文件名。
BIN  = ../slinktool

# 定义了两个变量，SRCS 和 OBJS。SRCS 中包含了所有的源文件名，OBJS 中包含了所有的目标文件名。这里使用了一个简单的替换规则，将所有的 .c 文件替换成了 .o 文件。
SRCS = dsarchive.c archive.c slinkxml.c slinktool.cpp
OBJS = $(SRCS:.c=.o)


# 定义了一个名为 all 的伪目标，用于指定生成所有目标文件。
all: $(BIN)

# 定义了一个生成最终目标文件的规则。该规则指定了如何将所有的目标文件链接成一个可执行文件。
$(BIN): $(OBJS)
	$(CXX) -o $(BIN) $(OBJS) $(LDFLAGS) $(LDLIBS)

# Standard object building
# 定义了一个生成目标文件的规则。该规则指定了如何将每个源文件编译成一个目标文件。
.c.o:
	$(CXX) $(CFLAGS) -c $< -o $@

# 定义了一个名为 clean 的伪目标，用于删除所有生成的目标文件和二进制文件。
clean:
	rm -f $(OBJS) $(BIN)

# 定义了一个名为 install 的伪目标，用于安装生成的二进制文件和 man 页面。这里只是输出一条消息，提示用户手动复制文件。
install:
	@echo
	@echo "No install method, copy the binary and man page yourself"
	@echo
