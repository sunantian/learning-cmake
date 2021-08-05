
1. Minimal working project with all source and header files under git control : working.

2. Generate hw_generated.h from the CMakeLists.txt

	Ref section 17.3 book Commands that generate files.

	add_custom_command(OUTPUT output1
				COMMAND command1
				[many options]
			)

	Note caveats : particularly if the build may be parallel.
