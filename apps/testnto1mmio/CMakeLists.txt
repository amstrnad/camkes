#
# Copyright 2018, Data61
# Commonwealth Scientific and Industrial Research Organisation (CSIRO)
# ABN 41 687 119 230.
#
# This software may be distributed and modified according to the terms of
# the BSD 2-Clause license. Note that NO WARRANTY is provided.
# See "LICENSE_BSD2.txt" for details.
#
# @TAG(DATA61_BSD)
#

cmake_minimum_required(VERSION 3.7.2)

project(testnto1mmio C)

# CAmkES spec is hard coded for the sabre
if(
    NOT
    "${KernelArch}"
    STREQUAL
    "arm"
    OR
        NOT
        "${KernelARMPlatform}"
        STREQUAL
        "sabre"
)
    message(FATAL_ERROR "testnto1mmio application only supported on Arm sabre")
endif()

DeclareCAmkESComponent(Driver1 SOURCES driver1.c INCLUDES .)
DeclareCAmkESComponent(Driver2 SOURCES driver2.c INCLUDES .)

DeclareCAmkESRootserver(testnto1mmio.camkes)
add_simulate_test([=[
    wait_for "hello from drv1"
    wait_for "hello from drv2"
]=])
