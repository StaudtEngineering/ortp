############################################################################
# CMakeLists.txt
# Copyright (C) 2014  Belledonne Communications, Grenoble France
#
############################################################################
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
#
############################################################################

if (NOT IOS)
	set(EXECUTABLES rtpsend rtprecv mrtpsend mrtprecv test_timer tevrtpsend tevrtprecv rtpsend_stupid)
	foreach(executable ${EXECUTABLES})
		bc_apply_compile_flags(${executable}.c STRICT_OPTIONS_CPP STRICT_OPTIONS_C)
		add_executable(${executable} ${executable}.c)
		target_link_libraries(${executable} ortp ${BCTOOLBOX_CORE_LIBRARIES})
	endforeach()

	install(TARGETS ${EXECUTABLES}
                RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
		PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
	)
endif()
