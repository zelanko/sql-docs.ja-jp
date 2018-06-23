---
title: クエリをデザイン |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
caps.latest.revision: 39
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 2ca850de7e8f09f704434910ccf0fa45cbfca726
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176562"
---
# <a name="design-the-query"></a>クエリのデザイン
  レポート ウィザードのこのページを使用すると、手動での入力、クエリ ビルダーでの対話的な操作、他のレポートからのインポートのいずれかの手段でクエリを作成できます。  
  
 [データ ソースを選択します] ページ (レポート ウィザードの前のページ) で選択したデータ ソースの種類によって、このページで入力できるクエリが決まります。 たとえば、データ ソースの種類が [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の場合、 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントまたはストアド プロシージャ名を入力できます。 データ ソースの種類が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の場合、クエリ ペインが無効になるので、直接クエリを入力できません。 クエリ ビルダーでクエリを指定できます。  
  
## <a name="options"></a>および  
 **クエリ文字列**  
 レポートで使用するデータを取得するためのクエリを入力します。  
  
 **クエリ ビルダー**  
 **[クエリ ビルダー]** をクリックすると、データ ソース用のクエリ デザイナーが開きます。他のレポートからクエリをインポートすることもできます。  
  
 クエリ デザイナーの詳細については、「 [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md)」を参照してください。  
  
## <a name="example"></a>例  
 データ ソースの種類の**Microsoft SQL Server**、次のクエリから姓の一覧の取得、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベース`Person`テーブル。  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 データ ソースの種類の**Microsoft SQL Server**、次のクエリの実行、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]ストアド プロシージャ`uspGetEmployeeManagers`id の従業員の番号は 1。  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a>参照  
 [レポート ウィザードのヘルプ](../../2014/reporting-services/report-wizard-help.md)   
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [レポートにデータを追加&#40;レポート ビルダーおよび SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  