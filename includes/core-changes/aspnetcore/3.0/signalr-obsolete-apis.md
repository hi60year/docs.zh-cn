---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394227"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="9e543-101">SignalR：UseSignalR 和 UseConnections 方法被标记为过时</span><span class="sxs-lookup"><span data-stu-id="9e543-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="9e543-102">在 ASP.NET Core 3.0 中，方法 `UseConnections` 和 `UseSignalR` 以及类 `ConnectionsRouteBuilder` 和 `HubRouteBuilder` 被标记为过时。</span><span class="sxs-lookup"><span data-stu-id="9e543-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9e543-103">引入的版本</span><span class="sxs-lookup"><span data-stu-id="9e543-103">Version introduced</span></span>

<span data-ttu-id="9e543-104">3.0</span><span class="sxs-lookup"><span data-stu-id="9e543-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9e543-105">旧行为</span><span class="sxs-lookup"><span data-stu-id="9e543-105">Old behavior</span></span>

<span data-ttu-id="9e543-106">SignalR 中心路由是使用 `UseSignalR` 或 `UseConnections` 配置的。</span><span class="sxs-lookup"><span data-stu-id="9e543-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9e543-107">新行为</span><span class="sxs-lookup"><span data-stu-id="9e543-107">New behavior</span></span>

<span data-ttu-id="9e543-108">配置路由的旧方法已弃用，并已替换为终结点路由。</span><span class="sxs-lookup"><span data-stu-id="9e543-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9e543-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="9e543-109">Reason for change</span></span>

<span data-ttu-id="9e543-110">正在将中间件移动到新的终结点路由系统。</span><span class="sxs-lookup"><span data-stu-id="9e543-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="9e543-111">添加中间件的旧方法即将过时。</span><span class="sxs-lookup"><span data-stu-id="9e543-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9e543-112">建议的操作</span><span class="sxs-lookup"><span data-stu-id="9e543-112">Recommended action</span></span>

<span data-ttu-id="9e543-113">将 `UseSignalR` 替换为 `UseEndpoints`：</span><span class="sxs-lookup"><span data-stu-id="9e543-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="9e543-114">**旧代码：**</span><span class="sxs-lookup"><span data-stu-id="9e543-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="9e543-115">**新代码：**</span><span class="sxs-lookup"><span data-stu-id="9e543-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="9e543-116">类别</span><span class="sxs-lookup"><span data-stu-id="9e543-116">Category</span></span>

<span data-ttu-id="9e543-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9e543-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9e543-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9e543-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->