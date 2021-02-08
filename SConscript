import os
from pathlib import Path

LIBRARY = 'freertos-simulator.a'
INCLUDES = ['.','Kernel', 'Kernel/include', 'Kernel/portable/ThirdParty/GCC/Posix', 
            'Kernel/portabl/ThirdParty/GCC/Posix/utils', 'Demo/Common/include']

Import('freertos_env')
print(freertos_env['CPPPATH'])
freertos_env['CPPPATH'] += INCLUDES

sources = Glob('Kernel/*.c') + [File(f) for f in [
    'simulator_main.c',
    # Memory manager (use malloc() / free() )
    'Kernel/portable/MemMang/heap_3.c',
    # posix port
    'Kernel/portable/ThirdParty/GCC/Posix/utils/wait_for_event.c',
    'Kernel/portable/ThirdParty/GCC/Posix/port.c',
    # Demo library.
    'Demo/Common/Minimal/AbortDelay.c',
    'Demo/Common/Minimal/BlockQ.c',
    'Demo/Common/Minimal/blocktim.c',
    'Demo/Common/Minimal/countsem.c',
    'Demo/Common/Minimal/death.c',
    'Demo/Common/Minimal/dynamic.c',
    'Demo/Common/Minimal/EventGroupsDemo.c',
    'Demo/Common/Minimal/flop.c',
    'Demo/Common/Minimal/GenQTest.c',
    'Demo/Common/Minimal/integer.c',
    'Demo/Common/Minimal/IntSemTest.c',
    'Demo/Common/Minimal/MessageBufferAMP.c',
    'Demo/Common/Minimal/MessageBufferDemo.c',
    'Demo/Common/Minimal/PollQ.c',
    'Demo/Common/Minimal/QPeek.c',
    'Demo/Common/Minimal/QueueOverwrite.c',
    'Demo/Common/Minimal/QueueSet.c',
    'Demo/Common/Minimal/QueueSetPolling.c',
    'Demo/Common/Minimal/recmutex.c',
    'Demo/Common/Minimal/semtest.c',
    'Demo/Common/Minimal/StaticAllocation.c',
    'Demo/Common/Minimal/StreamBufferDemo.c',
    'Demo/Common/Minimal/StreamBufferInterrupt.c',
    'Demo/Common/Minimal/TaskNotify.c',
    'Demo/Common/Minimal/TimerDemo.c',
]]


lib = freertos_env.Library(LIBRARY, sources)

result = (lib, list(map(lambda x: os.path.join(os.getcwd(), x), INCLUDES)))
Return('result')