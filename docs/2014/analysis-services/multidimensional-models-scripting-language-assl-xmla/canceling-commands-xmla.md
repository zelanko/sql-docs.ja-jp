---
title: コマンドのキャンセル (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 003c70362c38ae1838b4679abf6485fa031a9143
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545064"
---
# <a name="canceling-commands-xmla"></a>コマンドのキャンセル (XMLA)
  コマンドを発行するユーザーの管理アクセス許可によっては、XML for Analysis (XMLA) の[Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)コマンドを使用して、セッション、セッション、接続、サーバープロセス、または関連付けられたセッションまたは接続に対してコマンドを取り消すことができます。  
  
## <a name="canceling-commands"></a>コマンドのキャンセル  
 プロパティを指定せずに `Cancel` コマンドを送信することにより、ユーザーは現在の明示的なセッションのコンテキスト内で現在実行中のコマンドをキャンセルできます。  
  
> [!NOTE]  
>  暗黙のセッション内で実行中のコマンドは、ユーザー操作によって取り消すことはできません。  
  
### <a name="canceling-batch-commands"></a>バッチ コマンドのキャンセル  
 ユーザーが `Batch` コマンドを取り消した場合、`Batch` コマンド内に残っている未実行のコマンドはすべて取り消されます。 `Batch` コマンドがトランザクション型であれば、`Cancel` コマンドの実行前に実行されたすべてのコマンドはロールバックされます。  
  
## <a name="canceling-sessions"></a>セッションのキャンセル  
 コマンドの[SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)プロパティに明示的なセッションのセッション識別子を指定することによって `Cancel` 、データベース管理者またはサーバー管理者は、現在実行中のコマンドを含め、セッションを取り消すことができます。 データベース管理者は、自分が管理権限を持つデータベースに対するセッションだけをキャンセルできます。  
  
 データベース管理者は、DISCOVER_SESSIONS スキーマ行セットを取得することにより、指定されたデータベースに対するアクティブ セッションを取得することができます。 データベース管理者は、DISCOVER_SESSIONS スキーマ行セットを取得するために、XMLA メソッドを使用 `Discover` して、メソッドの restriction プロパティの[Restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) SESSION_CURRENT_DATABASE restriction 列に適切なデータベース識別子を指定し `Discover` ます。  
  
## <a name="canceling-connections"></a>接続のキャンセル  
 コマンドの[ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla)プロパティで接続識別子を指定することにより、 `Cancel` サーバー管理者は、実行中のすべてのコマンドを含め、特定の接続に関連付けられているすべてのセッションをキャンセルし、接続を取り消すことができます。  
  
> [!NOTE]  
>  のインスタンスが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続に関連付けられたセッションを特定およびキャンセルできない場合 (HTTP 接続を提供している間にデータポンプが複数のセッションを開いた場合など)、インスタンスは接続を取り消すことができません。 `Cancel` コマンドの実行中にこのような状況が生じた場合には、エラーが発生します。  
  
 サーバー管理者は XMLA の `Discover` メソッドを使用して DISCOVER_CONNECTIONS スキーマ行セットを取得することにより、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのアクティブな接続を取得できます。  
  
## <a name="canceling-server-processes"></a>サーバー プロセスのキャンセル  
 サーバー管理者は、コマンドの[spid](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)プロパティにサーバープロセス識別子 (spid) を指定することにより、 `Cancel` 特定の spid に関連付けられているコマンドを取り消すことができます。  
  
## <a name="canceling-associated-sessions-and-connections"></a>関連するセッションおよび接続のキャンセル  
 [Cancelassociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla)プロパティを true に設定すると、コマンドで指定された接続、セッション、または SPID に関連付けられている接続、セッション、およびコマンドを取り消すことができ `Cancel` ます。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;Discover メソッド](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
