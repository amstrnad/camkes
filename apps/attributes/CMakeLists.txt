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

project(attributes C)

DeclareCAmkESComponent(foo SOURCES foo.c)
DeclareCAmkESComponent(bar SOURCES bar.c)
DeclareCAmkESComponent(baz)

DeclareCAmkESRootserver(attributes.camkes)
add_simulate_test([=[
    wait_for "a = 11, b = 1"
    wait_for "c = 5, d = 4"
]=])
