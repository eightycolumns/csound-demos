abspath_to_makefile := $(abspath $(lastword $(MAKEFILE_LIST)))
makefile_dir := $(patsubst %/,%,$(dir $(abspath_to_makefile)))

title := demo-03
wav_file := $(makefile_dir)/$(title).wav

.PHONY: all
all: $(wav_file)

orchestra := $(makefile_dir)/orchestra
score := $(makefile_dir)/score

subdirs := aux bus instrument osc part plugin util

includes := $(foreach subdir,$(subdirs),$(wildcard $(makefile_dir)/$(subdir)/*))

csound_flags := -B 1024 -b 245 --dither --ksmps=1 -m 135 -s -r 44100

$(wav_file): $(orchestra) $(score) $(includes)
	csound $(csound_flags) -o $(title).wav -W $(orchestra) $(score)
