---
title: クエリの設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 4ce60e8326149ac0d8e7f54a84dd344f5088ee3d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56032620"
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
  
 データ ソースの種類の**Microsoft SQL Server**、次のクエリの実行、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]ストアド プロシージャ`uspGetEmployeeManagers`従業員 id 番号は 1。  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a>参照  
 [レポート ウィザードのヘルプ](../../2014/reporting-services/report-wizard-help.md)   
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [レポートにデータを追加&#40;レポート ビルダーおよび SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
