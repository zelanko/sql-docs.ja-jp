---
title: "Data Streaming Destination を構成する |Microsoft ドキュメント"
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL11.DTS.DESIGNER.DATASTREAMINGDEST.F1
ms.assetid: bcdbb833-20c8-47ff-a641-bb517f9a1af3
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3ef9bf1887ec05effe76c456011bac71b370eb3b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="configure-data-streaming-destination"></a>Data Streaming Destination を構成する
  **[Data Streaming Destination の詳細エディター]** ダイアログ ボックスを使用して、Data Streaming Destination を構成します。 このダイアログ ボックスを開くには、コンポーネントをダブルクリックするか、データ フロー デザイナーでコンポーネントを右クリックしてから **[編集]**をクリックします。  
  
 このダイアログ ボックスには、 **[コンポーネントのプロパティ]**、 **[入力列]**、 **[入力プロパティと出力プロパティ]**の 3 つのタブがあります。  
  
## <a name="component-properties-tab"></a>[コンポーネントのプロパティ] タブ  
 このタブには、次の編集可能なフィールドがあります。  
  
|フィールド|説明|  
|-----------|-----------------|  
|名前|パッケージ内の Data Streaming Destination コンポーネントの名前です。|  
|[ValidateExternalMetadata]|デザイン時に外部データ ソースを使用してコンポーネントを検証するかどうかを示します。 false に設定した場合、外部データ ソースに対する検証は実行時まで遅延されます。|  
|IDColumnName|データ フィード公開ウィザードによって生成されたビューには、この追加の ID 列があります。 ID 列は、データが他のアプリケーションによって OData フィードとして使用された場合に、データ フローからの出力データの EntityKey として機能します。<br /><br /> この列の既定の名前は _ID です。 この ID 列には別の名前を指定できます。|  
  
## <a name="input-columns-tab"></a>[入力列] タブ  
 このタブの上部ペインに、使用可能な入力列がすべて表示されます。 このコンポーネントの出力に含める列を選択します。 選択した列は、下部ペインの一覧に表示されます。 この一覧の **[出力の別名]** フィールドに新しい名前を入力することにより、出力列の名前を変更できます。  
  
## <a name="input-output-properties-tab"></a>[入力プロパティと出力プロパティ] タブ  
 [入力列] タブと同様に、このタブの出力列の名前は変更できます。 左側のツリー ビューで、 **[Data Streaming Destination の入力]** 、 **[入力列]**の順に展開します。 入力列の名前をクリックし、右ペインで出力列の名前を変更します。  
  
## <a name="see-also"></a>参照  
 [Data Streaming Destination](../../integration-services/data-flow/data-streaming-destination.md)   
 [チュートリアル: SSIS パッケージを SQL ビューとして公開する](../../integration-services/data-flow/walkthrough-publish-an-ssis-package-as-a-sql-view.md)  
  
  
