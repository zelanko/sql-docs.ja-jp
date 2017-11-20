---
title: "ディメンション テーブルおよびキー (緩やかに変化するディメンション ウィザード) を選択して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 24413b539223f32d8ee808d584bb1a629f3f7e23
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>[ディメンション テーブルおよびキーの選択]\ (緩やかに変化するディメンション ウィザード)
  **[ディメンション テーブルおよびキーの選択]** ページを使用すると、読み込むディメンション テーブルを選択できます。 データ フローの列を、読み込み対象の列にマップします。  
  
 このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[ODBC 入力先エディター]**  
 一覧から既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして OLE DB 接続マネージャーを作成します。  
  
> [!NOTE]  
>  緩やかに変化するディメンション ウィザードでは、OLE DB 接続マネージャーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]への接続のみがサポートされます。  
  
 **[新規作成]**  
 **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して既存の接続マネージャを選択するか、 **[新規作成]** をクリックして新しい OLE DB 接続を作成します。  
  
 **[テーブルまたはビュー]**  
 一覧からテーブルまたはビューを選択します。  
  
 **[入力列]**  
 マッピングを指定する入力列を一覧から選択します。  
  
 **[ディメンション列]**  
 使用できるすべてのディメンション列を表示します。  
  
 **[キーの種類]**  
 ビジネス キーとして使用するディメンション列を 1 つ選択します。 ビジネス キーを必ず 1 つ指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [出力を緩やかに変化するディメンション ウィザードを使用して構成します。](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  

