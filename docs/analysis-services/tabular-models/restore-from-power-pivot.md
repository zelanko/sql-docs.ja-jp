---
title: "Power Pivot から復元 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 88cd0379f0d23f819ab362a273c58bb40db81fa9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="restore-from-power-pivot"></a>Power Pivot から復元
  SQL Server Management Studio の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] から復元機能を使って、テーブル モードで実行されている Analysis Services インスタンス上に新しいテーブル モデル データベースを作成したり、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブック (.xlsx) から既存のデータベースに復元したりできます。  
  
> [!NOTE]  
>  SQL Server Data Tools の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] からのインポート プロジェクト テンプレートが同様の機能を提供します。 詳細については、「 [Power Pivot からのインポート (SSAS テーブル)](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)」を参照してください。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]から復元機能を使用する場合、次の点に注意してください。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]から復元機能を使用するには、サーバー管理者ロールのメンバーとして Analysis Services インスタンスにログオンしている必要があります。  
  
-   Analysis Services インスタンス サービス アカウントには、復元するブック ファイルの読み取り権限が必要です。  
  
-   既定では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]からデータベースを復元する場合は、テーブル モデル データベースのデータ ソースの権限借用情報プロパティは既定値に設定されており、Analysis Services インスタンス サービス アカウントを指定します。 権限借用の資格情報をデータベース プロパティの Windows ユーザー アカウントに変更することをお勧めします。 詳細については、「[権限借用 (SSAS テーブル)](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)」を参照してください。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ モデルのデータは、Analysis Services インスタンス上の既存または新規のテーブル モデル データベースにコピーされます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックにリンク テーブルが含まれている場合は、新規テーブルを使用して作成されたテーブルのように、データ ソースを使用せずにテーブルとして再作成されます。  
  
### <a name="to-restore-from-power-pivot"></a>Power Pivot から復元するには  
  
1.  SSMS で、復元先の Active Directory インスタンスで **[データベース]** を右クリックし、**[[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] から復元]** をクリックします。  
  
2.  **[[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] から復元]** ダイアログ ボックスで、**[復元元]** の **[バックアップ ファイル]** で **[参照]** をクリックし、復元する .abf または .xslx ファイルを選択します。  
  
3.  **[復元対象]**の **[データベースの復元]**で、新しいデータベースまたは既存のデータベースの名前を入力します。 名前を指定しない場合は、ブック名が使用されます。  
  
4.  **[ストレージの場所]**で、 **[参照]**をクリックし、データベースを格納する場所を選択します。  
  
5.  **[オプション]**で、 **[セキュリティ情報を含める]** チェック ボックスをオンのままにします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックから復元する場合は、この設定は適用されません。  
  
## <a name="see-also"></a>参照  
 [表形式モデルのデータベース (SSAS 表形式)](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)   
 [Power Pivot からのインポート (SSAS テーブル)](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)  
  
  
