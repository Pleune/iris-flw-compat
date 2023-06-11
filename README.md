<p align="center"><img src="https://i.imgur.com/Pt8G6kF.png" alt="Logo" width="200"></p>
<h1 align="center">Iris & Oculus Flywheel Compat<br>
	<a href="https://www.curseforge.com/minecraft/mc-mods/iris-flywheel-compat"><img src="http://cf.way2muchnoise.eu/659897.svg" alt="CF"></a>
  <a href="https://www.curseforge.com/minecraft/mc-mods/iris-flywheel-compat/files"><img src="https://cf.way2muchnoise.eu/versions/For%20MC_659897_all.svg" alt="Supported Versions"></a>
  <a href="https://github.com/leon-o/iris-flw-compat/blob/main/LICENSE"><img src="https://img.shields.io/github/license/leon-o/iris-flw-compat" alt="License"></a>
    <br><br>
</h1>

# Iris & Oculus Flywheel Compat
Allow Flywheel instancing optimization to be enabled when using iris.

# Principle
Flywheel uses a method called GPU Instancing to render entities. It is very efficient when rendering a large number of repeating entities (e.g. gears in Create mod). But when you use iris and enable shaderpack, this optimization is disabled. Because flywheel needs to use its own shader to render these entities and flywheel's shader will no longer work when you enable shaderpack.

This mod will automatically merge flywheel's shader with the shader in shaderpack when shaderpack is enabled to be able to render entities using Instancing.

When you have a large number of entities to render, there is a huge CPU bottleneck with the original rendering method.

# Implementation details

This mod replaces the ProgramCompiler::getProgram method. When Flywheel trys to generate shaders, this mod will merge the shader generated by flywheel with the gbuffer_block shader in the shaderpack.

# Credit
This project uses the [glsl-transformer](https://github.com/IrisShaders/glsl-transformer) to transformer the shaders.
