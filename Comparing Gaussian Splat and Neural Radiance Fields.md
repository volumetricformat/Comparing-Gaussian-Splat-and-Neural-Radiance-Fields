## Introduction
This knowledge paper aims to provide a high-level comparison between two recent and promising advanced techniques in novel view synthesis: Gaussian Splats and Neural Radiance Fields (NeRF).

### Basic Mechanisms

**Gaussian Splat**
- Primary Use: Novel View Synthesis. 
- Methodology: Train explicit (Gaussian) primitives to recreate a scene from novel viewpoints. Instead of learning colors at a point can be thought of as learning the gaussian primitive extent surrounding a point dependent on the view into a scene. Doesn’t use ray casting and uses rasterization to render primitives. Generates a view by rendering the gaussian primitives from back-to-front (ie splatting).
- Compatibility with graphics pipelines: Uses explicit graphics primitives which allow the use of a traditional graphics pipelines in the rendering process. This allows techniques like particle effects for transitions etc. 
- Performance: 

**Neural Radiance Fields (NeRF)**
- Primary Use: Novel View Synthesis. 
- Methodology: Uses AI to learn a neural radiance field that implicitly maps any viewing direction and point in a continuous volume to the corresponding color and density value. Uses volume rendering techniques like ray marching to sample the radiance field yielding the color and density.
- Compatibility with graphics pipelines: Introduces a neural inference component within the graphics/render pipeline to implicitly map the view direction and point in space to a color and density. 
- Performance: The implicit neural graphics/renderer pipeline requires extra computation relative to traditional graphics pipelines.

### Latest Research and Acceleration and Optimizations techniques
Both Gaussian Splats and Neural Radiance Fields are evolving rapidly with new research yielding improvements over existing implementations.Of particular note is: 
- Nvidia's Instant-NGP implementation which significantly optimizes NeRF training, making it close to real-time on GPUs. The recent addition of Adaptive Shells also significantly improves rendering and quality. 
- The Compact3D research from the University of California, Davis provides very significant data size reduction for Gaussian Splats.

### Data Size Implications
Both techniques require original camera images for training reconstruction, and likewise both techniques also are able to minimize the size of  data needed for synthesizing novel views.

### Conclusion
Gaussian Splats and Neural Radiance Fields represent two sophisticated approaches in the realm of novel view synthesis. While Gaussian Splat offers compatibility with traditional graphics pipelines, NeRF, especially in its Instant-NGP implementation, provides enhanced rendering quality and efficiency, albeit with specific hardware requirements. The choice between these methods depends on the specific requirements of the project, including considerations of data size, texture quality, and available hardware.

**Comparison Table: Gaussian Splat vs. Neural Radiance Fields**
| Feature   | Gaussian Splat | Neural Radiance Fields (NeRF) |
| --------- | ----- | ------------- | 
| Primary Use | Novel View Synthesis | Novel View Synthesis | 
| Methodology | Uses explicit Gaussian primitives to represent scene | Uses AI to learn mapping between and point in a continuous volume combined with view to radiance | 
| Compatibility with Graphics Pipelines | Compatible with traditional explicit primitive based graphics pipelines | Uses implicit neural rendering introducing additional computation | 
| Training Time | Long | Short | 
| Hardware Requirements | Nothing specific | GPU Acceleration | 
| Data Size | Smaller data sizes | Smaller data sizes | 

### About the Volumetric Format Association
The [Volumetric Format Association](https://www.volumetricformat.org/) is driving the development of volumetric video as the next revolution for content creation, editing 3D content, distribution of 3D content and creating entirely new ways to tell stories and communicate with each other.
