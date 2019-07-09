---
title: ユーザーを切断 Analysis Services サーバーとセッション |Microsoft Docs
ms.date: 07/05/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 696c6548dadda2412566acf7fae1e2cff2b28095
ms.sourcegitcommit: 9af07bd57b76a34d3447e9e15f8bd3b17709140a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624398"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a>Analysis Services サーバー上のユーザーとセッションの切断
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]
  管理者は、ワークロード管理の一環としてユーザー操作を終了する可能性があります。 ユーザー操作を終了するには、セッションと接続を取り消します。 セッションは、クエリの実行時に自動的に作成される場合 (暗黙的) と、管理者が作成時に名前を付ける場合 (明示的) があります。 接続は、クエリを実行できる開かれたパイプのようなものです。 セッションと接続は両方とも、アクティブなときに終了できます。 たとえば、処理に時間が長すぎる場合、または実行されているコマンドが正常に書き込まれたかどうかについていくつかの疑問が生じた場合は、セッションの処理を終了する可能性があります。  
  
## <a name="ending-sessions-and-connections"></a>セッションと接続の終了  
 セッションと接続を管理するには、動的管理ビュー (Dmv) および XMLA を使用します。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、Analysis Services インスタンスに接続します。  
  
2.  現在実行中のすべてのセッション、接続、およびコマンドのリストを取得するには、次のいずれかの DMV クエリを MDX クエリ ウィンドウに貼り付けます。  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  (このクエリは Azure Analysis Services には適用されません)
  
     `Select * from $System.Discover_Commands`  
  
3.  F5 キーを押してクエリを実行します。  
  
     DMV クエリは、セッションと接続の情報を、読み取りやコピーが容易な表形式の結果セットとして返します。  
  
 クエリ ウィンドウを開いた状態にします。 次の手順では、切断するセッションの SPID をコピーするために、このページに戻ります。  
  
 セッションを終了するために、XMLA クエリ ウィンドウをもう 1 つ開きます。  
  
1.  次の構文を MDX クエリ ウィンドウに貼り付けます。ConnectionID、SessionID、または SPID プレースホルダーは、前の手順からコピーした有効な値に置き換えてください。  
  
    ```  
    <Cancel xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  F5 キーを押してキャンセル コマンドを実行します。  

SPID/SessionID をキャンセルすると、SPID/セッション Id に対応するセッションで実行されているすべてのアクティブなコマンドが取り消されます。 接続のキャンセルとを接続に関連付けられたセッションを特定し、そのセッションで実行されているすべてのアクティブなコマンドをキャンセルします。 まれに、エンジンは、すべてのセッションおよび Spid; の接続に関連付けられているを追跡できない場合、接続は閉じられないたとえば、複数のセッションが HTTP シナリオでを開きます。   
  
このトピックで参照された XMLA の詳細については、次を参照してください。[メソッドの実行&#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)と[Cancel 要素&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)します。  
  
## <a name="see-also"></a>参照  
 [接続およびセッションの管理 (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [BeginSession 要素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla)   
 [EndSession 要素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla)   
 [Session 要素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
