![SpaceXpanse logo](./Src/SpaceXpanse/Bitmaps/banner.png)
 
# SpaceXpanse Metaverse Simulator

SpaceXpanse is a simulator based on Newtonian mechanics. Its playground
is our solar system with many of its major bodies – the sun, planets and moons.
You take control of a spacecraft – either historic, hypothetical, or purely
science fiction. SpaceXpanse is unlike most commercial computer games with a space
theme – there are no predefined missions to complete (except the ones you set
yourself), no aliens to destroy and no goods to trade. Instead, you will get a
pretty good idea about what is involved in real space flight – how to plan an
ascent into orbit, how to rendezvous with a space station, or how to fly to
another planet. It is more difficult, but also more of a challenge. Some people
get hooked, others get bored. Finding out for yourself is easy – simply give it
a try. SpaceXpanse is free, so you don’t need to invest more than a bit of your
spare time.

## License 

SpaceXpanse is now published as an Open Source project under the MIT License (see
[LICENSE](./LICENSE) file for details).

D3D9Client graphics engine is licensed under LGPL, see [LGPL](./OVP/D3D9Client/LGPL.txt)

## Installation

Get the SpaceXpanse source repository from github
```bash
git clone git@github.com:spacexpanse/metaverse.git
```
or
```bash
git clone https://github.com/spacexpanse/metaverse.git
```

To configure and generate the makefiles, you need a recent
[CMake](https://cmake.org/download/).

To compile SpaceXpanse from its sources, you need
[Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/).
SpaceXpanse has been successfully built with VS Community 2019, but other versions should
also work. Note that VS2019 comes with built-in CMake support, so you don't
need a separate CMake installation.

Some configuration caveats:
- If you are using the [Ninja](https://cmake.org/cmake/help/latest/generator/Ninja.html)
generator (default for the VS built-in CMake), you may also need
[vspkg](https://github.com/microsoft/vcpkg) to configure the VS toolset.
- If you are using the VS2019 generator, you may need to set up Visual Studio to use
only a single thread for the build. This is because some of the build tools (especially
those for generating the SpaceXpanse documentation) are not threadsafe, and the VS2019
generator doesn't understand the CMake JOB_POOL directive.

SpaceXpanse is a 32-bit application. Be sure to configure vspkg and CMake accordingly.

If you want to build the documentation, you need a few additional tools:
- a filter to convert ODT and DOC sources to PDF, such as
  [LibreOffice](https://www.libreoffice.org/download/download/).
- a LaTeX compiler suite such as [MiKTeX](https://miktex.org/download).
- [Doxygen](https://www.doxygen.nl/index.html) for building the source-level
  documentation for developers.

By default, the build is configured to create both graphics flavours of the
SpaceXpanse executable (although this can be configured with the SPACEXPANSE_GRAPHICS CMake flag):
- ``spacexpanse.exe`` is the standalone SpaceXpanse application with built-in DX7 graphics.
- ``spacexpanse_ng.exe`` is a launcher for ``./Modules/Server/spacexpanse.exe`` which is the
graphics server version of SpaceXpanse. It requires an external graphics client
plugin to be loaded via the Modules tab of the SpaceXpanse Launchpad dialog.
The reference D3D7Client is included with the build with essentially the same
functionality as the built-in graphics version. Use 3rd party client
implementations to make use of more modern graphics engines.

See [README.compile](./README.compile) for details on building SpaceXpanse.

## Planet textures

The SpaceXpanse git repository does not include most of the planetary texture files
required for running SpaceXpanse.
You need to install those separately. The easiest way to do so is by installing
[SpaceXpanse Metaverse](https://github.com/spacexpanse/metaverse). Optionally you can
also install high-resolution versions of the textures from the SpaceXpanse website.
You should keep the SpaceXpanse installation separate from your SpaceXpanse git
repository.

To configure SpaceXpanse to use the texture installation, set the
SPACEXPANSE_PLANET_TEXTURE_INSTALL_DIR entry in CMake. For example, if SpaceXpanse 
was installed in `C:\SpaceXpanse`, the CMake option should be set to
`C:/SpaceXpanse/Textures`.
Alternatively, you can configure the texture directory after building SpaceXpanse
by setting the `PlanetTexDir` entry in `SpaceXpanse.cfg`.

## Help

Help files are located in the Doc subfolder (if you built them). SpaceXpanse.pdf is the
main SpaceXpanse user manual.

The in-game help system can be opened via the "Help" button on
the SpaceXpanse Launchpad dialog, or with Alt-F1 while running
SpaceXpanse.

Remaining questions can be posted on the SpaceXpanse user forum at
[forum.spacexpanse.org](https://forum.spacexpanse.org).
