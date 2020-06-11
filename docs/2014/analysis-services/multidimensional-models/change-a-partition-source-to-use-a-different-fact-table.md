---
title: 別のファクトテーブルを使用するようにパーティションソースを変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0063a6023d769dc6dccd616655d10e0bd3c65a98
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537171"
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a>別のファクト テーブルを使用するためのパーティション ソースの変更
  キューブのパーティションを作成する場合、複数のファクト テーブルを使用するように選択できます。 複数のテーブルは、単一のデータ ソース ビュー、複数のデータ ソース ビュー、または複数のデータ ソースから得たものである場合があります。 データ ソース ビューには、複数のデータ ソースから得た複数のテーブルが含まれている場合もあります。  
  
 キューブのパーティションのファクト テーブルとディメンションはすべて、キューブのファクト テーブルおよびディメンションと同一構造であることが必要です。 たとえば、同一構造の複数のファクト テーブルに、異なる年度のデータや異なる製品ラインのデータを格納できます。  
  
 ファクト テーブルはパーティション ウィザードの **[基になる情報の指定]** で指定します。 このページの **[検索対象]** の横の [パーティション ソース] で、検索するデータ ソースまたはデータ ソース ビューを指定します。 次に、 **[テーブルの検索]** をクリックし、 **[使用できるテーブル]** で使用するテーブルを選択します。  
  
 複数のファクト テーブルを使用する場合は、パーティション間でデータが重複していないことを確認してください。 たとえば、あるファクト テーブルに 2012 年のトランザクションのみが含まれ、別のファクト テーブルに 2013 年のトランザクションのみが含まれる場合、これらのテーブルに含まれるデータは重複しません。 同様に、異なる製品ラインや異なる地域のファクト テーブルにも重複データは含まれません。  
  
 重複データを含む複数のファクト テーブルを使用することは可能ですが、お勧めはできません。 使用する場合は、パーティション内でフィルターを使用して、あるパーティションで使用されるデータが、別のパーティションで使用されないようにする必要があります。 詳細については、「 [ローカル パーティションの作成と管理 (Analysis Services)](create-and-manage-a-local-partition-analysis-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ローカル パーティションの作成と管理 (Analysis Services)](create-and-manage-a-local-partition-analysis-services.md)  
  
  
