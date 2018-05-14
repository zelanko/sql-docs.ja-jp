---
title: SSDT での DirectQuery モードを有効にする |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1d2a1ced9638a48dc02729c0f224b883974a7dde
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="enable-directquery-mode-in-ssdt"></a>SSDT での DirectQuery モードの有効化
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
このトピックでは、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でテーブル モデル プロジェクトに対して DirectQuery モードを有効にする方法を説明します。  
  
SSDT で設計するテーブル モデルに対して DirectQuery モードを有効にすると、次のようになります。
-   DirectQuery モードと互換性のない機能が無効になります。  
-   既存のモデルが検証されます。 機能が DirectQuery モードと互換性がない場合は、警告が表示されます。  
-   DirectQuery モードを有効にする前にデータが既にインポートされている場合は、作業モデルのキャッシュが空になります。  
  
### <a name="enable-directquery"></a>DirectQuery の有効化  
  
SSDT の **[Model.bim]** ファイルの **[プロパティ]** ペインで、プロパティの **[DirectQuery モード]** を **[オン]** に変更します。  

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
  
