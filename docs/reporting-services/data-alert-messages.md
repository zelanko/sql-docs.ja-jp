---
title: "データ警告メッセージ |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6819720c-d848-4b90-9b51-89501b4f4645
caps.latest.revision: 9
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: a192628a5f2f899e96753d98e210bca6bfd426f1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="data-alert-messages"></a>データ警告メッセージ

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services のデータ警告は、電子メールでの 2 種類のデータ警告メッセージを配信します。 データとメッセージをアラートの結果とエラーの説明を持つメッセージ。 結果を含むメッセージは、すべての受信者に共通して関係し、かつ業務意思決定にとって重要なレポート データの変更について情報を提供します。 何かの理由でエラーが発生し、結果情報が取得できない場合は、代わりにエラー メッセージが送信されます。

データ警告定義の所有者は、データ警告マネージャーで、データ警告インスタンスに関する情報を参照することもできます。 詳細については、「 [SharePoint ユーザー用のデータ警告マネージャー](../reporting-services/data-alert-manager-for-sharepoint-users.md)」を参照してください。  

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。
  
##  <a name="DataAlertMessages"></a> データ警告メッセージ  
 次に示すのは、結果を含むデータ警告メッセージと、エラー説明を含む警告メッセージのスクリーン ショットです。  
  
 **結果メッセージ**  
  
 ![結果を含むデータ警告電子メール メッセージ](../reporting-services/media/rs-alertmessageresults.gif "結果を含むデータ警告電子メール メッセージ")  
  
 **エラー メッセージ**  
  
 ![データ警告メッセージのエラー メッセージで](../reporting-services/media/rs-alertmessageerrror.gif "データ警告メッセージとエラー メッセージ")  
  
 これらのメッセージには、共通の情報項目が含まれます。  
  
1.  **[代理]** には、データ警告定義の作成者の名前が表示されます。  
  
2.  警告定義内に説明を入力した場合は、 **[代理]**の下に説明が表示されます。  
  
3.  **[警告結果]** には、警告定義で指定されたルールを満たすレポート データ フィード内の行が表形式で表示されるか、またはエラー説明が表示されます。 表示される行数に制限はありません。  
  
4.  **[レポートに移動する]** は、警告定義の作成対象であるレポートへのリンクです。 レポートが移動または削除されたためにリンクが無効になっている場合は、エラー メッセージが表示されます。  
  
5.  **[ルール]** には、警告定義内のルールと句がリストされます。 この情報は、警告結果を検証および理解したり、変更したい警告定義内のルールを識別して、結果の範囲を絞り込んだり広げたりするのに役立ちます。  
  
6.  **[レポート パラメーター]** には、レポートの実行時に使用されたパラメーターとパラメーター値がリストされます。 パラメーターとパラメーター値は、警告結果を理解するのに役立ちます。  
  
7.  **[コンテキスト値]** には、レポート データ領域の外部にあるレポート アイテムの名前と値がリストされます。 これらのアイテムは通常、テキスト ボックスです。 たとえば、定数値 (レポートの件名や説明など) を格納したテキスト ボックスなどが該当します。  
  
 2 つのメッセージ型の間で唯一異なるのは、項目 5 ( **警告結果**) です。 データ警告インスタンスまたはデータ警告メッセージの作成時にエラーが発生した場合は、問題を説明するエラー メッセージが **[警告結果]** に表示されます。 エラー メッセージ (すべての受信者に送信される) は、業務上の意思決定に有効または必要な警告結果が利用できないことを受信者に知らせます。  
  
  
##  <a name="HowTo"></a> 関連タスク  
 データ警告メッセージ内に表示される情報の多くを提供する、データ警告定義を作成および編集するための手順を紹介しているトピックの一覧を次に示します。  
  
-   [データ警告デザイナーでデータ警告を作成します。](../reporting-services/create-a-data-alert-in-data-alert-designer.md)  
  
-   [警告デザイナーでデータ警告を編集します。](../reporting-services/edit-a-data-alert-in-alert-designer.md)  

## <a name="see-also"></a>参照

[データ警告デザイナー](../reporting-services/data-alert-designer.md)   
[Reporting Services のデータ警告](../reporting-services/reporting-services-data-alerts.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
