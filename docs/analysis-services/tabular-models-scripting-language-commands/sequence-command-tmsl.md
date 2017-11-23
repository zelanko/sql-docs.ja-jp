---
title: "シーケンス コマンド (TMSL) |Microsoft ドキュメント"
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
ms.assetid: 898d6ec2-9b40-441b-be2b-5728d1d2882e
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6fe2e7416c4c86b926f30295b6fe2f75a334751f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sequence-command-tmsl"></a>Sequence コマンド (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  使用して、**シーケンス**バッチ モードで Analysis Services のインスタンスで、連続する一連の操作を実行するコマンド。  コマンド全体とすべてのコンポーネントが成功するトランザクションの順序で完了する必要があります。  
  
 次のコマンドを実行することができます、順番を除く、**更新**複数のオブジェクトを同時に処理を並列で実行されるコマンドです。  
  
-   [コマンド &#40; を作成します。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)  
  
-   [CreateOrReplace コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)  
  
-   [Alter コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)  
  
-   [コマンド &#40; を削除します。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)  
  
-   [更新コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)  
  
-   [Backup コマンドと #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)  
  
-   [復元コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)  
  
-   [Attach コマンドと #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)  
  
-   [コマンド &#40; をデタッチします。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)  
  
## <a name="request"></a>要求  
 **maxParallelism**を決定する省略可能なプロパティかどうか**更新**順次または並列的に操作が実行されます。  
  
 既定の動作では、できるだけ多くの並列処理を使用します。 埋め込むことによって**更新**内**シーケンス**操作を 1 つのスレッドの制限を含む、処理中に使用されるスレッドの正確な数を制御できます。  
  
> [!NOTE]  
>  割り当てられた整数**maxParallelism**処理中に使用するスレッドの最大数を決定します。 有効な値は、正の整数です。 値は、1 は並列でありません (1 つのスレッドを使用する) に設定します。  
  
 のみ**更新**を並列に実行します。 変更した場合**maxParallelism**使用するには、固定数のスレッドを確認して、プロパティで、[コマンド &#40; を更新TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)潜在的な影響を理解します。 使用できる複数のスレッドになっている場合でも、並列処理を損なうようにプロパティを設定することができます。 次の一連の更新の種類では、並列処理の最適な程度を提供します。  
  
-   まず、ClearValues を使用してすべてのオブジェクトの更新を指定します。  
  
-   次に、更新を DataOnly を使用してすべてのオブジェクトの指定します。  
  
-   フル、Calculate、自動、または追加を使用してすべてのオブジェクトの最終更新を指定します。  
  
 これですべてのバリエーションが並列処理を中断します。  
  
```  
{   
  "sequence":    
    {   
      "maxParallelism": 3,   
      "operations": [   
        {   
          "mergepartitions": {   
            "sources": [   
              {   
                "database": "salesdatabase",   
                "table": "Sales",   
                "partition": "partition1"   
              },   
              {   
                "database": "salesdatabase",   
                "table": "Sales",   
                "partition": "partition2"   
              }   
            ]   
          }   
        },   
        {   
          "refresh": {   
            "type": "calculate",   
            "object": {   
             "database": "salesdatabase"   
            }   
          }   
        }   
      ]   
    }      
}   
```  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からは、このコマンドの既製のスクリプトを生成することはできません。 代わりに、例を使用して開始したり、独自に作成できます。  
  
 [ \[MS-t SSAS\]: SQL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855)ドキュメントには、JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 が含まれています。. 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください ([表形式モデル スクリプト言語 &#40;です。TMSL &#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) がサポートされているものより明確にします。  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
