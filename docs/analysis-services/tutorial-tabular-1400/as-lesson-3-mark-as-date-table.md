---
title: 'Analysis Services チュートリアル-レッスン 3: 日付テーブルとしてマーク |Microsoft Docs'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 282103baa0283e46e31b9ffe6b837e90e4bfac3c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43069399"
---
# <a name="mark-as-date-table"></a>日付テーブルとしてマーク

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

レッスン 2: データの取得、インポートしたという名前のディメンション テーブル**DimDate**します。 モデルでこのテーブルは DimDate と命名、中にそのことができますとも呼ばれます、*日付テーブル*日付と時刻のデータが含まれていることにします。  
  
含むプロパティを指定する必要があります、後でメジャーを作成する場合のように、DAX タイム インテリジェンス関数を使用するたびに、*日付テーブル*および一意の識別子*日付列*そのテーブルにします。
  
このレッスンでマークする、 **DimDate**テーブルとして、*日付テーブル*と**日付**テーブルの列 (日付) として、*日付列*(一意識別子) です。  

日付テーブルと日付列をマークする前に、モデルを理解しやすくする少しハウスキーピングを実行するよい機会になります。 DimDate テーブルという名前の列がわかります**FullDateAlternateKey**します。 この列には、毎日、テーブルに含まれる各カレンダー年の 1 つの行が含まれています。 メジャーの数式とレポートに、この列を多く使用します。 しかし、FullDateAlternateKey はこのコラムの優れた識別子では実際にありません。 名前を変更する**日付**、簡単に識別し、式に含めることができます。 可能であればは、SSDT でのクライアント レポート アプリケーションを識別しやすいようにするテーブルと列のようなオブジェクトの名前を変更することをお勧めです。 
  
このレッスンを完了するまでに時間を推定: **3 分**  
  
## <a name="prerequisites"></a>Prerequisites  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 2: データを取得する](../tutorial-tabular-1400/as-lesson-2-get-data.md)します。 

### <a name="to-rename-the-fulldatealternatekey-column"></a>FullDateAlternateKey 列の名前を変更するには

1.  モデル デザイナーで、クリックして、 **DimDate**テーブル。

2.  ヘッダーをダブルクリック、 **FullDateAlternateKey**列に名前を変更し、**日付**。

  
### <a name="to-set-mark-as-date-table"></a>日付テーブルとして設定する  
  
1.  **[日付]** 列を選択し、 **[プロパティ]** ウィンドウの **[データ型]** で  **[日付]** が必ず選択されているようにします。  
  
2.  **[テーブル]** メニュー、**[日付]****[日付テーブルとしてマーク]** の順にクリックします。  
  
3.  **[日付テーブルとしてマーク]** ダイアログ ボックスの **[日付]** ボックスの一覧で、一意の識別子として **[Date]** 列を選択します。 これは通常、既定で選択します。 **[OK]** をクリックします。 

    ![as-lesson3-date-table](../tutorial-tabular-1400/media/as-lesson3-date-table.png)
  

## <a name="whats-next"></a>次の操作

[レッスン 4: リレーションシップの作成](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)です。
  
