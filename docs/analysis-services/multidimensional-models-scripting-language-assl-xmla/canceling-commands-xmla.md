---
title: "コマンド (XMLA) のキャンセル |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
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
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d86c304f8735cc8933fd9c466af4f58f4d980c74
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="canceling-commands-xmla"></a>コマンドのキャンセル (XMLA)
  コマンドを実行しているユーザーの管理権限に応じて、[キャンセル](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)Analysis (XMLA) は、セッション、セッション、接続、サーバー プロセス、または関連付けられているセッションでコマンドを取り消すことができますの XML でコマンドまたは接続です。  
  
## <a name="canceling-commands"></a>コマンドのキャンセル  
 ユーザーが送信することによって、現在の明示的なセッションのコンテキスト内で現在実行中のコマンドを取り消すことができます、**キャンセル**コマンド プロパティを指定せずにします。  
  
> [!NOTE]  
>  暗黙のセッション内で実行中のコマンドは、ユーザー操作によって取り消すことはできません。  
  
### <a name="canceling-batch-commands"></a>バッチ コマンドのキャンセル  
 ユーザーが取り消された場合、**バッチ**コマンド、し、残りのすべてのコマンド内で実行されていない、**バッチ**コマンドが取り消されました。 場合、**バッチ**コマンドがトランザクション型でいずれかのコマンドの前に実行されたこと、**キャンセル**コマンドの実行がロールバックされます。  
  
## <a name="canceling-sessions"></a>セッションのキャンセル  
 明示的なセッションのセッション識別子を指定することによって、 [SessionID](../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)のプロパティ、**キャンセル**コマンドでは、データベース管理者またはサーバー管理者は、セッションを取り消すことができますも含め、現在のコマンドを実行しています。 データベース管理者は、自分が管理権限を持つデータベースに対するセッションだけをキャンセルできます。  
  
 データベース管理者は、DISCOVER_SESSIONS スキーマ行セットを取得することにより、指定されたデータベースに対するアクティブ セッションを取得することができます。 データベース管理者が、XMLA を使用する、DISCOVER_SESSIONS スキーマ行セットを取得する**Discover**メソッド、のSESSION_CURRENT_DATABASE制限列の適切なデータベース識別子を指定して[制限](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)のプロパティ、 **Discover**メソッドです。  
  
## <a name="canceling-connections"></a>接続のキャンセル  
 接続識別子を指定することによって、 [ConnectionID](../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)のプロパティ、**キャンセル**コマンド、サーバー管理者は、すべてのすべてを含む特定の接続に関連付けられているセッションを取り消すことができます、コマンドを実行し、接続をキャンセルします。  
  
> [!NOTE]  
>  場合、インスタンスの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]見つけてデータ ポンプでは、HTTP 接続しつつ、複数のセッションが開いたら、インスタンスが接続を取り消すことはできませんの接続に関連付けられているセッションを取り消すことはできません。 この場合が実行中に発生した場合、**キャンセル**コマンドでエラーが発生します。  
  
 サーバー管理者のアクティブな接続を取得できる、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA を使用して DISCOVER_CONNECTIONS スキーマ行セットを取得することによってインスタンス**Discover**メソッドです。  
  
## <a name="canceling-server-processes"></a>サーバー プロセスのキャンセル  
 サーバー プロセス識別子 (SPID) を指定することによって、 [SPID](../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)のプロパティ、**キャンセル**コマンド、サーバー管理者は、特定の SPID に関連付けられているコマンドを取り消すことができます。  
  
## <a name="canceling-associated-sessions-and-connections"></a>関連するセッションおよび接続のキャンセル  
 設定することができます、 [CancelAssociated](../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)プロパティ接続、セッション、および接続、セッション、またはで指定した SPID に関連付けられているコマンドをキャンセルする場合は true を**キャンセル**コマンド。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を検出します。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
