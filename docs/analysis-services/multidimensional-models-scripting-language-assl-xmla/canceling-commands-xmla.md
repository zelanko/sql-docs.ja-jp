---
title: コマンド (XMLA) のキャンセル |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 077d6b14f87cf7207c9a81486a3efc30ab4772c4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
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
 [Discover メソッド&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
