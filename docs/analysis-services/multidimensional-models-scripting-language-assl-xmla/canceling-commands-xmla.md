---
title: コマンドのキャンセル (XMLA) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 313708ad1575c7b9922ac796791d0d623c51b54b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63182941"
---
# <a name="canceling-commands-xmla"></a>コマンドのキャンセル (XMLA)
  コマンドを発行したユーザーの管理アクセス許可に応じて、[キャンセル](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)Analysis (XMLA) は、コマンドをキャンセルして、セッション、セッション、接続、サーバー プロセス、または、関連付けられているセッションでの XML でコマンドまたは接続します。  
  
## <a name="canceling-commands"></a>コマンドのキャンセル  
 ユーザーが送信することによって、現在の明示的なセッションのコンテキスト内で現在実行中のコマンドをキャンセルできます、**キャンセル**コマンド プロパティを指定せずにします。  
  
> [!NOTE]  
>  暗黙のセッション内で実行中のコマンドは、ユーザー操作によって取り消すことはできません。  
  
### <a name="canceling-batch-commands"></a>バッチ コマンドのキャンセル  
 ユーザーがキャンセルした場合、**バッチ**コマンドを次に残りのすべてのコマンドを内で実行されていない、**バッチ**コマンドが取り消されました。 場合、**バッチ**コマンドがトランザクション型でいずれかのコマンドの前に実行されたが、**キャンセル**コマンドの実行がロールバックされます。  
  
## <a name="canceling-sessions"></a>セッションのキャンセル  
 明示的なセッションのセッション識別子を指定することによって、 [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)のプロパティ、**キャンセル**コマンドをデータベース管理者またはサーバー管理者がセッションをキャンセルなど、現在のコマンドを実行します。 データベース管理者は、自分が管理権限を持つデータベースに対するセッションだけをキャンセルできます。  
  
 データベース管理者は、DISCOVER_SESSIONS スキーマ行セットを取得することにより、指定されたデータベースに対するアクティブ セッションを取得することができます。 データベース管理者が、XMLA を使用するには、DISCOVER_SESSIONS スキーマ行セットを取得するには、 **Discover**メソッドをのSESSION_CURRENT_DATABASE制限列の適切なデータベースの識別子を指定します[。制限](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla)のプロパティ、 **Discover**メソッド。  
  
## <a name="canceling-connections"></a>接続のキャンセル  
 接続識別子を指定することによって、 [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla)のプロパティ、**キャンセル**コマンド、サーバー管理者は、すべてのセッションをすべて含む、特定の接続に関連付けられているをキャンセルできます、コマンドを実行し、接続をキャンセルします。  
  
> [!NOTE]
>  場合、インスタンスの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]見つけてインスタンスが接続を取り消すことはできません、データ ポンプでは、HTTP 接続を提供しながら複数のセッションが開いたらなど、接続に関連付けられているセッションを取り消すことはできません。 このケースがの実行中に発生した場合、**キャンセル**コマンドでエラーが発生します。  
  
 サーバー管理者のアクティブな接続を取得できます、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、XMLA を使用して DISCOVER_CONNECTIONS スキーマ行セットを取得することによってインスタンス**Discover**メソッド。  
  
## <a name="canceling-server-processes"></a>サーバー プロセスのキャンセル  
 サーバー プロセス識別子 (SPID) を指定することによって、 [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)のプロパティ、**キャンセル**コマンド、サーバー管理者は、特定の SPID に関連付けられているコマンドを取り消すことができます。  
  
## <a name="canceling-associated-sessions-and-connections"></a>関連するセッションおよび接続のキャンセル  
 設定することができます、 [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla)プロパティを接続、セッション、および接続、セッション、またはで指定された SPID に関連付けられているコマンドをキャンセルする場合は true、**キャンセル**コマンド。  
  
## <a name="see-also"></a>参照  
 [Discover メソッド&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
