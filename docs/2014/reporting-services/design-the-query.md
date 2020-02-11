---
title: クエリのデザイン |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f09964013bdc8675e5d4701bd86421317c33fc97
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109292"
---
# <a name="design-the-query"></a>クエリのデザイン
  レポート ウィザードのこのページを使用すると、手動での入力、クエリ ビルダーでの対話的な操作、他のレポートからのインポートのいずれかの手段でクエリを作成できます。  
  
 [データ ソースを選択します] ページ (レポート ウィザードの前のページ) で選択したデータ ソースの種類によって、このページで入力できるクエリが決まります。 たとえば、データソースの種類が[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]である場合、ステートメントまた[!INCLUDE[tsql](../includes/tsql-md.md)]はストアドプロシージャ名を入力できます。 データソースの種類が[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の場合、クエリペインは無効になり、直接クエリを入力することはできません。 クエリ ビルダーでクエリを指定できます。  
  
## <a name="options"></a>オプション  
 **クエリ文字列**  
 レポートで使用するデータを取得するためのクエリを入力します。  
  
 **[クエリ ビルダー]**  
 
  **[クエリ ビルダー]** をクリックすると、データ ソース用のクエリ デザイナーが開きます。他のレポートからクエリをインポートすることもできます。  
  
 クエリ デザイナーの詳細については、「 [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md)」を参照してください。  
  
## <a name="example"></a>例  
 **Microsoft SQL Server**データソースの種類の場合、次のクエリでは、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベース`Person`テーブルから姓の一覧を取得します。  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 データソースの種類**Microsoft SQL Server**の場合、次のクエリで[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]は、 `uspGetEmployeeManagers`識別番号が1の従業員のストアドプロシージャを実行します。  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a>参照  
 [レポートウィザードのヘルプ](../../2014/reporting-services/report-wizard-help.md)   
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md)  
  
  
