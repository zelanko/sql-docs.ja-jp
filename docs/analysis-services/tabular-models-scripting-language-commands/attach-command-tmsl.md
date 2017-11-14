---
title: "Attach コマンド (TMSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7a12d148-eac9-4e6c-a222-1439e0817c64
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d19093c8030e9faf909168cd4707cf5b3e8759ef
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="attach-command-tmsl"></a>Attach コマンド (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Analysis Services のファイルをサーバーにアタッチします。  
  
  
## <a name="request"></a>要求  
  
```  
{   
   "attach":{   
      "folder":"C:\\Program Files\\Microsoft SQL Server\\MSAS13.Tabular\\OLAP\\Data\\",  
      "readWriteMode":"readOnly",  
      "password":"secret"  
   }  
}  
```  
  
 JSON で受け入れられるプロパティと、attach コマンドは次のようにします。  
  
||||  
|-|-|-|  
|**プロパティ**|**[Default]**|**Description**|  
|[データベース]|[必須]|アタッチするデータベース オブジェクトの名前。|  
|フォルダー|[必須]|アタッチされたデータベースを格納するフォルダー。|  
|パスワード|空|使用して、アタッチされたデータベースで機密データを暗号化するパスワードです。|  
|readWriteMode|読み取り/書き込み|データベースに許可されるアクセス モードを示す列挙値。<br /><br /> **列挙値は次のとおりです。**<br /><br /> – 読み取り/書き込み、読み取り/書き込みアクセスが許可されます。<br /><br /> – 読み取り専用、読み取り専用のアクセスが許可されます。<br /><br /> readOnlyExclusive –、読み取り専用の排他アクセスが許可されます。|  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からこのコマンドであらかじめ用意されているスクリプトを生成するには、データベースのアタッチ ダイアログ ボックスで スクリプト ボタンをクリックします。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください[表形式モデル スクリプト言語 & #40 です。TMSL &#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)明確にする新機能がサポートされている.  

## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Analysis Services データベースのインポートとデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  

