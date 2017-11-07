---
title: "接続およびセッション (XMLA) の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bc532f9097c8023fcdc160d597c2cd0830782891
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="managing-connections-and-sessions-xmla"></a>接続およびセッションの管理 (XMLA)
  *状態保持*id とメソッドの呼び出しの間のクライアントのコンテキスト、サーバーを保持する状態します。 *状態を保持しない*をサーバーが保存されていません id およびクライアントのコンテキストをメソッド呼び出しの完了後に、条件は、します。  
  
 XML for Analysis (XMLA) をサポートしている状態を保持する場合は、*セッション*一連のステートメントをまとめて実行するための使用が許可されます。 そのような一連のステートメントの例としては、後続のクエリで使用するための計算されるメンバーの作成があります。  
  
 一般に、XMLA のセッションは、OLE DB 2.6 の仕様で概説されている以下の動作に従います。  
  
-   セッションはトランザクションとコマンド コンテキストのスコープを定義します。  
  
-   複数のコマンドを単一のセッションのコンテキストで実行できます。  
  
-   経由で送信されるプロバイダー固有のコマンドは、XMLA のコンテキストにおけるトランザクションのサポート、 [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
 XMLA は、Distributed Authoring and Versioning (DAV) プロトコルが疎結合環境でロックを実装するために使用しているアプローチと同様の手法で、Web 環境のセッションをサポートする方法を定義します。 この実装は、プロバイダーがさまざまな理由 (たとえば、タイムアウトや接続エラーなど) でセッションの有効期限を終了させることができるという点で、DAV と類似しています。 セッションがサポートされる場合、Web サービスは、中断されて再開が必要なコマンドのセットを認識し、処理する準備を整えている必要があります。  
  
 World Wide Web Consortium (W3C) による Simple Object Access Protocol (SOAP) 仕様は、新しいプロトコルを作成するには SOAP メッセージの先頭に SOAP ヘッダーを使用することを推奨しています。 次の表は、XMLA がセッションの開始、維持、終了のために定義する SOAP ヘッダー要素と属性の一覧を示しています。  
  
|SOAP ヘッダー|Description|  
|-----------------|-----------------|  
|BeginSession|プロバイダーに新しいセッションの作成を要求します。 プロバイダーは、新しいセッションを作成し、SOAP 応答の Session ヘッダーの一部としてセッション ID を返すことによって応答します。|  
|SessionId|値域には、セッションの残りの部分での各メソッド呼び出しで使用する必要のあるセッション ID が含まれます。 プロバイダーは SOAP 応答の中でこのタグを送信します。クライアントも、Session ヘッダー要素ごとに、この属性を送信する必要があります。|  
|Session|このヘッダーは、セッションで生じるメソッド呼び出しごとに使用する必要があります。値域にはセッション ID が含まれている必要があります。|  
|EndSession|セッションを終了するには、このヘッダーを使用します。 セッション ID がこの値域に含まれている必要があります。|  
  
> [!NOTE]  
>  セッション ID は、そのセッションが引き続き有効であることを保証するものではありません。 セッションの有効期限が切れた場合 (たとえば、タイムアウトが生じた場合や、接続が失われた場合など)、プロバイダーはそのセッションのアクションを終了してロールバックすることができます。 その結果、同じセッション ID でのクライアントからの後続のメソッド呼び出しはすべて、セッションが有効でないことを示すエラーによって失敗します。 クライアントは、この状況に対処し、そのセッションのメソッド呼び出しを最初から再送信するよう準備する必要があります。  
  
## <a name="legacy-code-example"></a>レガシ コードの例  
 以下の例は、セッションがどのようにサポートされるかを示しています。  
  
1.  セッションを開始するには、クライアントからのアウトバウンド XMLA メソッド呼び出しに SOAP の BeginSession ヘッダーを追加します。 セッション ID がまだ不明なため、値域が最初は空白になっています。  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  プロバイダーからの SOAP 応答メッセージが含まれています、セッション ID には、戻り値のヘッダー領域で、XMLA ヘッダー タグを使用して\<SessionId >。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  セッションのメソッド呼び出しごとに、プロバイダーから返されたセッション ID を含む Session ヘッダーを追加する必要があります。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  セッションの完了時に、 \<EndSession > タグを使用すると、関連するセッション ID 値を格納します。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a>参照  
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

