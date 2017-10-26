---
title: "SSDT での DirectQuery モードを有効にする |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f3a5cfe3f2b39f35d2b2e70dd44ec11adeebcd0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="enable-directquery-mode-in-ssdt"></a>SSDT での DirectQuery モードの有効化

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

このトピックでは、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でテーブル モデル プロジェクトに対して DirectQuery モードを有効にする方法を説明します。  
  
SSDT で設計するテーブル モデルに対して DirectQuery モードを有効にすると、次のようになります。
-   DirectQuery モードと互換性のない機能が無効になります。  
-   既存のモデルが検証されます。 機能が DirectQuery モードと互換性がない場合は、警告が表示されます。  
-   DirectQuery モードを有効にする前にデータが既にインポートされている場合は、作業モデルのキャッシュが空になります。  
  
### <a name="enable-directquery"></a>DirectQuery の有効化  
  
SSDT の **[Model.bim]** ファイルの **[プロパティ]** ペインで、プロパティの **[DirectQuery モード]**を **[オン]**に変更します。  

![SSDT での DirectQuery モードの有効化](../../analysis-services/tabular-models/media/enable-directquery-mode-in-ssdt.png)
  
モデルが既にデータ ソースと既存のデータに接続されている場合は、リレーショナル データベースへの接続で使用したデータベース資格情報を入力するよう求められます。 モデル内の既存のデータは、メモリ内キャッシュから削除されます。  
  
DirectQuery モードを有効にする前にモデルが部分的または完全に完成している場合、互換性のない機能に関するエラーが発生する可能性があります。 Visual Studio で **[エラー一覧]** を開き、モデルが DirectQuery モードに切り替わるのを妨げている問題を解決します。  


### <a name="whats-next"></a>次の操作 
これで、テーブルのインポート ウィザードを使用してデータをインポートし、モデルのメタデータを取得できます。 データの行は取得しませんが、モデルの基礎として使用するテーブル、列、およびリレーションシップを取得します。 

テーブルごとにサンプル パーティションを作成し、サンプル データを追加できるため、作成時にモデルの動作を検証することができます。 追加したすべてのサンプル データは、 **[Excel で分析]** またはワークスペース データベースに接続できるその他のクライアント ツールで使用されます。 詳細については、「 [Design モードで DirectQuery モデルにサンプル データを追加する](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) 」を参照してください。  
  
> [!TIP]  
    >  空のモデルの DirectQuery モードでも、各テーブルの小規模な組み込み行セットをいつでも表示できます。 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[テーブル]** > **[テーブルのプロパティ]** の順にクリックすると、50 行データセットが表示されます。  
  
  
## <a name="see-also"></a>参照  
[SSMS での DirectQuery モードの有効化](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[Design モードで DirectQuery モデルにサンプル データを追加する](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)
  

