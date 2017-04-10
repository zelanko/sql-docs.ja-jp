---
title: "SQL Server 2016 の Analysis Services 機能における重大な変更 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "重大な変更 [Analysis Services]"
  - "Analysis Services のアップグレード"
ms.assetid: aeb02542-5a6c-458c-a110-13413dd3e9d9
caps.latest.revision: 55
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 53
---
# SQL Server 2016 の Analysis Services 機能における重大な変更
  *重大な変更* は、モデルまたはサーバーのアップグレード後に、データ モデル、アプリケーション コード、またはスクリプトが機能しなくなるような変更です。  
  
> [!NOTE]  
>  一方、 *動作の変更* は、モデルやアプリケーションが機能しなくなることのない、コードの変更という位置付けです。ただし、以前のリリースとは動作が変わります。  動作の変更の例としては、既定値の変更や、以前は許可されていたプロパティやオプションの構成の禁止などがあります。 このリリースでの動作の変更の詳細については、「 [Behavior Changes to Analysis Services Features in SQL Server 2016](../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md)」を参照してください。  
  
## .NET 4.0 のバージョン アップグレード  
 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] の Analysis Services 管理オブジェクト (AMO)、ADOMD.NET、およびテーブル モデル オブジェクト モデル (TOM) のクライアント ライブラリが .NET 4.0 ランタイムに対応するようになりました。 これは、.NET 3.5 をターゲットとするアプリケーションにとって重大な変更になる可能性があります。 これらのアセンブリの新しいバージョンを使用するアプリケーションは、.NET 4.0 以降をターゲットとする必要があります。  
  
## AMO のバージョン アップグレード  
 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] は [Analysis Services 管理オブジェクト &#40;AMO&#41;](../Topic/Analysis%20Services%20Management%20Objects%20\(AMO\).md) に対するバージョン アップグレードで、特定の環境では重大な変更になります。  以前のバージョンからアップグレードした場合でも、AMO を呼び出す既存のコードやスクリプトは従来と同様に動作します。 ただし、アプリケーションを *再コンパイル* する必要がある場合や [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] インスタンスを対象としている場合、コードやスクリプトを機能させるには、次の名前空間を追加する必要があります。  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 コードで Microsoft.AnalysisServices アセンブリを参照するときは常に [Microsoft.AnalysisServices.Core](../Topic/Microsoft.AnalysisServices.Core.md) 名前空間が必要になりました。 以前は **Microsoft.AnalysisServices** 名前空間のみに含まれていたオブジェクトが、このリリースでは Core 名前空間に移動されています (オブジェクトがテーブルと多次元の両方のシナリオで同じように使用される場合)。  たとえば、サーバー関連の API は Core 名前空間に移動されました。  
  
 複数の名前空間が存在することになりますが、どちらも同じアセンブリ (Microsoft.AnalysisServices.dll) に含まれます。  
  
## XEvent DISCOVER の変更点  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の SSMS における XEvent DISCOVER のストリーミングに対するサポートを強化するために、`DISCOVER_XEVENT_TRACE_DEFINITION` が次の XEvent トレースに置き換えられました。  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  
  
## 参照  
 [Analysis Services の旧バージョンとの互換性](../analysis-services/analysis-services-backward-compatibility.md)  
  
  