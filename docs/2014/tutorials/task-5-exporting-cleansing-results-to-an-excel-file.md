---
title: 'タスク 5: クレンジング結果を Excel ファイルにエクスポートする |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3c690becefb71b71c154131b6957c1063872b540
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489126"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>タスク 5: Excel ファイルにクレンジングの結果をエクスポートする
  ここでは、クレンジング アクティビティから Excel ファイルに結果をエクスポートします。 詳細については、「[エクスポートステージ](https://msdn.microsoft.com/library/hh213061.aspx#Export)」を参照してください。  
  
1.  右ペインで、[**変換先の種類**] に [ **Excel** ] を選択します。  
  
2.  [**参照**] をクリックし、出力ファイル名として「**クレンジングされた仕入先リスト .xls**」を指定して、[**開く**] をクリックします。  
  
3.  クレンジングされたデータのみをエクスポートするには、**出力**形式に対して**のみデータ**を選択します。 2番目のオプションである [**データ] と [クレンジング情報**] を使用すると、クレンジングアクティビティの詳細とクレンジングされたデータをエクスポートできます。 [**形式の標準化**] オプションを使用すると、ドメインで定義したすべての出力形式を、そのドメインの値に適用できます。 チュートリアルのドメインには、出力形式を定義していません。  
  
     ![クレンジングの結果ページのエクスポート](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "クレンジングの結果ページのエクスポート")  
  
4.  [**エクスポート**] をクリックしてデータをエクスポートします。 まだ [**完了**] をクリックしないでください。  
  
5.  [**エクスポート**中] ダイアログボックスで [**閉じる**] をクリックします。  
  
6.  [**完了**] をクリックして活動を終了します。 [**完了**] をクリックする前に結果のエクスポートを忘れた場合は、 **DQS クライアント**のメインページで [**データ品質プロジェクトを開く**] をクリックし、プロジェクトの一覧から [**クレンジング Supplier list** ] を選択し、画面の下部にある [**次へ**] をクリックして、クレンジングプロセスの**エクスポート**ステージに移動します。 [**戻る**] ボタンをクリックして **、[管理] と [結果の表示**] タブに切り替えることもできます。  
  
7.  クレンジングされた**仕入先リスト .xls**を開き、次の手順を実行します。  
  
    1.  ワークシートで adventure-work.com を検索することによって、末尾が "adventure-work.com" (文字が ' ではない) の電子メールアドレスがないことを確認します。  
  
    2.  **Country**列に**USA**の値がないことを確認します。  
  
    3.  **ロサンゼルス**を検索し、**状態**が**CA**に設定されていることを確認します。  
  
    4.  「 **Co.**」、「 **Corp.**」、および「 **inc.**」という用語がないことを確認します。  
  
    5.  スプレッドシートから**Address Validation**列を削除し、excel ファイルを保存します。 この追加列は Address Validation 複合ドメインに対応します。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 6: Cleanse Supplier List プロジェクトから値をインポートする](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
