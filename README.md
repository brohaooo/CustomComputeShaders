# CustomComputeShader

A minimal Unreal Engine 5.3 project for adding and using a compute shader. Please refer to the original [repository](https://github.com/AyoubKhammassi/CustomComputeShaders) and his [article](https://medium.com/realities-io/using-compute-shaders-in-unreal-engine-4-f64bac65a907#id_token=eyJhbGciOiJSUzI1NiIsImtpZCI6ImVkODA2ZjE4NDJiNTg4MDU0YjE4YjY2OWRkMWEwOWE0ZjM2N2FmYzQiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL2FjY291bnRzLmdvb2dsZS5jb20iLCJhenAiOiIyMTYyOTYwMzU4MzQtazFrNnFlMDYwczJ0cDJhMmphbTRsamRjbXMwMHN0dGcuYXBwcy5nb29nbGV1c2VyY29udGVudC5jb20iLCJhdWQiOiIyMTYyOTYwMzU4MzQtazFrNnFlMDYwczJ0cDJhMmphbTRsamRjbXMwMHN0dGcuYXBwcy5nb29nbGV1c2VyY29udGVudC5jb20iLCJzdWIiOiIxMDA0NTAxNDk2OTUxNTY4NjQ5NzQiLCJlbWFpbCI6ImJyb2hhb29vQGdtYWlsLmNvbSIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJuYmYiOjE3MDgzODU5ODQsIm5hbWUiOiJYaW5oYW8gTGluIiwicGljdHVyZSI6Imh0dHBzOi8vbGgzLmdvb2dsZXVzZXJjb250ZW50LmNvbS9hL0FDZzhvY0luaEVQMXJ0cGFPejhsWHZ3Uk9kdWxaSWQ4N0ZWUWNGQ28zUmwxWFVMd01BPXM5Ni1jIiwiZ2l2ZW5fbmFtZSI6IlhpbmhhbyIsImZhbWlseV9uYW1lIjoiTGluIiwibG9jYWxlIjoiemgtQ04iLCJpYXQiOjE3MDgzODYyODQsImV4cCI6MTcwODM4OTg4NCwianRpIjoiMWI2MWVlY2FhMDZkZWIxYzNmM2U3ODM1YWU2ZGVhMDQ1MTA2MGFhMCJ9.ZF9mFPbfsIsrAaUSxP6PwDDxX61hIWoogolKNx5fONpQMZorizjXvmZ6rtvIDMlKdZjj5tCcflZmPdeBIz80Y6BIBDzY61-J8Vpx46QRP9fbMW07j8uACGQXhq8rSWKh8CAmRqobQbnmvid6V1F6tUrQr7la_lzj4ryCO8QtjABJJaigatIYSqsWLB7u-7mLS9_GhUHKQV1ZIvJ1pfZlX5OmubTaBsmaQiaf_RhFRkRl5GPGUyjpYU1utqcJ5EIfUAl1cC2xgeXdhyZyG_Ckk7SA3mbmI4KnlFVv4uzviDl1dBKDYhEEukfCQECeYmU8VkwRwA0dElVC8T0FRqRx5Q)

## Modules:
* **CustomComputeShader** : The primary game module
* **CustomShadersDeclarations** : The game module that contains all the code for adding and using the compute shader

##  Shaders:
* **WhiteNoiseCS** : A simple compute shader that renders white noise to a texture

## What I changed

Comparing with UE 5.2, UE 5.3 no longer support IPooledRenderTarget::GetRenderTargetItem(), there's no approach to get the protected **FSceneRenderTargetItem RenderTargetItem** member. So, I just derived a child class to re-define GetRenderTargetItem().

Another thing is that the original **FWhiteNoiseCSManager::UpdateParameters** doesn't check whether the new input needs a Render Target with different size, which causes the render target to be fixed during the editing time until restart the editor. So, I added the updation of UAV each time when Render Target size changes.
