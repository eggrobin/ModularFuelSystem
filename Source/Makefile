KSPDIR		:= ${HOME}/ksp/KSP_linux
MANAGED		:= ${KSPDIR}/KSP_Data/Managed
GAMEDATA	:= ${KSPDIR}/GameData
MODGAMEDATA  := ${GAMEDATA}/ModularFuelTanks
PLUGINDIR	:= ${MODGAMEDATA}/Plugins

TARGETS		:= modularFuelTanks.dll

MFT_FILES := \
    AssemblyInfo.cs				\
    HeatPump.cs					\
    ModularFuelTanks.cs			\
    ModularFuelPartModule.cs	\
    RefuelingPump.cs			\
	Settings.cs					\
	$e

RESGEN2	:= resgen2
GMCS	:= gmcs
GIT		:= git
TAR		:= tar
ZIP		:= zip

all: version ${TARGETS}

.PHONY: version
version:
	@./git-version.sh

info:
	@echo "Modular Fuel Tanks Build Information"
	@echo "    resgen2:  ${RESGEN2}"
	@echo "    gmcs:     ${GMCS}"
	@echo "    git:      ${GIT}"
	@echo "    tar:      ${TAR}"
	@echo "    zip:      ${ZIP}"
	@echo "    KSP Data: ${KSPDIR}"
	@echo "    Plugin:   ${PLUGINDIR}"

modularFuelTanks.dll: ${MFT_FILES}
	${GMCS} -t:library -lib:${MANAGED} \
		-r:Assembly-CSharp,Assembly-CSharp-firstpass,UnityEngine \
		-out:$@ $^

clean:
	rm -f ${TARGETS} AssemblyInfo.cs

install: all
	mkdir -p ${PLUGINDIR}
	cp ${TARGETS} ${PLUGINDIR}

.PHONY: all clean install
