---
title: "多対多リレーションシップの割り当て (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- relationships [SQL Server], many-to-many
- junction tables [SQL Server]
- many-to-many relationships [SQL Server]
- mapping many-to-many relationships [SQL Server]
- database diagrams [SQL Server], relationships
ms.assetid: 2977cf92-98b5-48b2-b0fd-8fbc7040f2b4
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 393483c566c3e4b61833972ef2b33ba2dde8404a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/18/2017

---
# <a name="map-many-to-many-relationships-visual-database-tools"></a>多対多リレーションシップの割り当て (Visual Database Tools)
多対多リレーションシップを使用すると、テーブルの各行を他のテーブルの複数の行と関連付けることができます。 たとえば、 `authors` テーブルと `titles` テーブルとの間に多対多リレーションシップを作成し、各著者をその全著作に対応付け、各著作をすべての著者に対応付けることができます。 一方のテーブルから一対多リレーションシップを作成すると、各著作には著者が 1 人しか存在しない、または各著者には 1 冊の著作しかないという情報が誤って示されることになります。  
  
テーブル間の多対多リレーションシップは、それぞれのデータベースで交差テーブルによって実現できます。 交差テーブルには、関連付ける 2 つのテーブルの各主キー列が格納されます。 これを使用して、2 つのテーブルの各主キー列から、交差テーブル内の対応する列へのリレーションシップを作成します。 pubs データベースでは、 `titleauthor` テーブルが交差テーブルです。  
  
### <a name="to-create-a-many-to-many-relationship-between-tables"></a>テーブル間で多対多リレーションシップを作成するには  
  
1.  データベース ダイアグラムで、多対多リレーションシップを作成する各テーブルを追加します。  
  
2.  ダイアグラムを右クリックし、ショートカット メニューの **[新しいテーブル]** をクリックして 3 つ目のテーブルを作成します。 これが交差テーブルになります。  
  
3.  **[名前の選択]** ダイアログ ボックスで、システムによって割り当てられたテーブル名を変更します。 たとえば、 `titles` テーブルと `authors` テーブルとの間の交差テーブルは、現在 `titleauthors`という名前です。  
  
4.  2 つのテーブルの各主キー列を交差テーブルにコピーします。 他の列も、他のテーブルに追加するのと同様に交差テーブルに追加できます。  
  
5.  交差テーブルで、他の 2 つのテーブルの主キーをすべて含めて主キーを設定します。 詳細については、「 [方法 : 主キーを作成する (Visual Database Tools)](http://msdn.microsoft.com/en-us/85c623ca-4656-4d70-a9db-ee4d897cd214)」を参照してください。  
  
6.  2 つの各主テーブルと交差テーブルとの間に一対多リレーションシップを定義します。 交差テーブルは、作成するリレーションシップの "多" 側に配置します。 詳細については、「 [方法 : テーブル間にリレーションシップを作成する](http://msdn.microsoft.com/en-us/867a54b8-5be4-46e6-9702-49ae6dabf67c)」を参照してください。  
  
    > [!NOTE]  
    > データベース ダイアグラムで交差テーブルを作成しても、関連テーブルから交差テーブルにデータは挿入されません。 テーブルにデータを挿入する方法については、「[方法 : 複製挿入クエリを作成する (Visual Database Tools)](../../ssms/visual-db-tools/create-insert-results-queries-visual-database-tools.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[データベース ダイアグラムの使用 (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
  

