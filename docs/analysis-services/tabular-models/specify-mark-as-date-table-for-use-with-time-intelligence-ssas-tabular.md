---
title: 日付テーブルとしてマーク の指定 |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f6a4ad929c866658ce241f33ddd2a5326dc78e19
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039787"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence"></a>日付テーブルとしてマーク タイム インテリジェンスで使用するための指定します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  DAX の数式でタイム インテリジェンス関数を使用するために、日付テーブルと Date データ型の一意識別子 (datetime) 列を指定する必要があります。 日付テーブルの列が一意の識別子として指定されている場合は、日付テーブル内の列と任意のファクト テーブルのリレーションシップを作成できます。  
  
 タイム インテリジェンス関数を使用する場合は、次の規則が適用されます。  
  
-   DAX タイム インテリジェンス関数を使用する場合、ファクト テーブルから datetime 列を指定することはありません。 1 つ以上の datetime 列 (Date データ型で、一意の値を持つ) を含む独立した日付テーブルをモデル内に必ず作成する。  
  
-   日付テーブルの日付の範囲が連続している。  
  
-   日付テーブル内の datetime 列の粒度は日単位 (1 日未満の時間を含まない) にする。  
  
-   **[日付テーブルとしてマーク]** ダイアログ ボックスを使用して、日付テーブルと一意識別子列を指定する必要がある。  
  
-   日付テーブル内の Date データ型の列とファクト テーブルの間にリレーションシップを作成する。  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a>日付テーブルと一意識別子を指定するには  
  
1.  モデル デザイナーで、日付テーブルをクリックします。  
  
2.  **[テーブル]** メニュー、 **[日付]**、 **Mark as [日付] [テーブル]** の順にクリックします。  
  
3.  **[日付テーブルとしてマーク]** ダイアログ ボックスの **[日付]** ボックスの一覧で、一意識別子として使用する列を選択します。 この列は、一意の値を含んでいる必要があり、Date データ型である必要があります。 以下に例を示します。  
  
    |日付|  
    |----------|  
    |7/1/2010 12:00:00 AM|  
    |7/2/2010 12:00:00 AM|  
    |7/3/2010 12:00:00 AM|  
    |7/4/2010 12:00:00 AM|  
    |7/5/2010 12:00:00 AM|  
  
4.  必要に応じて、ファクト テーブルと日付テーブルの間のリレーションシップを作成します。  
  
## <a name="see-also"></a>参照  
 [計算](../../analysis-services/tabular-models/calculations-ssas-tabular.md)   
 [タイム インテリジェンス関数 (DAX)](http://msdn.microsoft.com/en-us/91df278d-4b28-40c1-a572-cdb91f081517)  
  
  
