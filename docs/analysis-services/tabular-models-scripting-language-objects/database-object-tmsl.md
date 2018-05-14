---
title: データベース オブジェクト (TMSL) |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9da6d97236811aaa0ef8ee757c7b2773bdda496a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="database-object-tmsl"></a>データベース オブジェクト (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  同じレベルのモデルに基づく表形式データベース互換性レベル 1200 以上を定義します。 このトピックでは、作成、変更、削除、およびデータベースの管理タスクを実行した要求のペイロードを提供する、データベースのオブジェクト定義を説明します。  
  
> [!NOTE]  
>  任意のスクリプトでは、時にデータベースを 1 つだけを参照できます。 データベース自体以外の任意のオブジェクトのデータベースのプロパティは、モデルを指定する場合は省略可能です。 モデルとを明示的に提供されている場合は、データベース名を推測するために使用するデータベースの間の一対一のマッピングがあります。   
> 同様に、データベースでそのプロパティを設定するモデルを省略できます。  
  
## <a name="object-definition"></a>オブジェクトの定義  
 すべてのオブジェクトは、共通の名前、型、説明、プロパティのコレクション、および注釈を含むプロパティのセットを持ちます。 **データベース**オブジェクトでは、次のプロパティもがあります。  
  
 compatibilitylevel  
 現在、有効な値は、1200 1400 です。 下位の互換性レベルは、さまざまなメタデータ エンジンを使用します。  
  
 readwritemode  
 データベースのモードを列挙します。 データベースを高可用性やスケーラビリティの構成では読み取り専用にすることはありません。 有効な値は readWrite、  
                読み取り専用、  
                または、readOnlyExclusive します。 参照してください[高可用性とスケーラビリティの Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)と[Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)詳細については、このプロパティを使用する場合。  
  
## <a name="usage"></a>使用方法  
 **データベース**オブジェクトは、ほぼすべてのコマンドで使用します。 参照してください[で表形式モデル スクリプト言語コマンド&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md)一覧についてはします。 A**データベース**サーバー オブジェクトの子であるオブジェクト。  
  
 作成する場合、置換、またはデータベース オブジェクトを変更することは、オブジェクト定義のすべての読み取り/書き込みプロパティを指定します。 読み取り/書き込みプロパティの省略は、削除であると見なされます。  
  
## <a name="partial-syntax"></a>一部の構文  
 このオブジェクトの定義が非常に大きいため、直接プロパティのみが一覧表示されます。 **モデル**オブジェクトはデータベースの定義の大部分を提供します。 参照してください[モデル オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)オブジェクトの定義方法にします。  
  
```  
    "database": {  
      "type": "object",  
      "properties": {  
        "name": {  
          "type": "string"  
        },  
        "id": {  
          "type": "string"  
        },  
        "description": {  
          "type": "string"  
        },  
        "compatibilityLevel": {  
          "type": "integer"  
        },  
        "readWriteMode": {  
          "enum": [  
            "readWrite",  
            "readOnly",  
            "readOnlyExclusive"  
          ]  
        },  
        "model": {  
          "type": "object",  
          ...  
        }  
    }  
  
```  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [高可用性とスケーラビリティの Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)  
  
  
