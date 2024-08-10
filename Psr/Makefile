FILES = AbstractLogger.php              \
        InvalidArgumentException.php    \
        LoggerAwareInterface.php        \
        LoggerAwareTrait.php            \
        LoggerInterface.php             \
        LoggerTrait.php                 \
        LogLevel.php                    \
        NullLogger.php

BPCPHP_FILES = $(patsubst %,Log/%,$(FILES))

libpsr-log.so:
	rm -rf Log
	mkdir Log
	for i in $(FILES); do phptobpc ../src/$$i > Log/$$i; done
	bpc -v \
		-c bpc.conf  \
		-l psr-log \
		placeholder-log.php \
		$(BPCPHP_FILES)

install-libpsr-log:
	bpc -l psr-log --install
