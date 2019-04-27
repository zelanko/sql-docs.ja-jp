---
title: Analysis Services での Power Pivot から復元 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 75290c6b877c3bb10cd42fbb10f1c087310791d3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472252"
---
# <a name="restore-from-power-pivot"></a>Power Pivot から復元
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  SQL Server Management Studio の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] から復元機能を使って、テーブル モードで実行されている Analysis Services インスタンス上に新しいテーブル モデル データベースを作成したり、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブック (.xlsx) から既存のデータベースに復元したりできます。  
  
> [!NOTE]  
>  SQL Server Data Tools の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] からのインポート プロジェクト テンプレートが同様の機能を提供します。 詳細については、次を参照してください。 [Power Pivot からのインポート](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)します。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]から復元機能を使用する場合、次の点に注意してください。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]から復元機能を使用するには、サーバー管理者ロールのメンバーとして Analysis Services インスタンスにログオンしている必要があります。  
  
-   Analysis Services インスタンス サービス アカウントには、復元するブック ファイルの読み取り権限が必要です。  
  
-   既定では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]からデータベースを復元する場合は、テーブル モデル データベースのデータ ソースの権限借用情報プロパティは既定値に設定されており、Analysis Services インスタンス サービス アカウントを指定します。 権限借用の資格情報をデータベース プロパティの Windows ユーザー アカウントに変更することをお勧めします。 詳細については、次を参照してください。[偽装](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)します。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ モデルのデータは、Analysis Services インスタンス上の既存または新規のテーブル モデル データベースにコピーされます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックにリンク テーブルが含まれている場合は、新規テーブルを使用して作成されたテーブルのように、データ ソースを使用せずにテーブルとして再作成されます。  
  
### <a name="to-restore-from-power-pivot"></a>Power Pivot から復元するには  
  
1.  SSMS で、復元先の Active Directory インスタンスで **[データベース]** を右クリックし、**[[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] から復元]** をクリックします。  
  
2.  **[[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] から復元]** ダイアログ ボックスで、**[復元元]** の **[バックアップ ファイル]** で **[参照]** をクリックし、復元する .abf または .xslx ファイルを選択します。  
  
3.  **[復元対象]** の **[データベースの復元]** で、新しいデータベースまたは既存のデータベースの名前を入力します。 名前を指定しない場合は、ブック名が使用されます。  
  
4.  **[ストレージの場所]** で、 **[参照]** をクリックし、データベースを格納する場所を選択します。  
  
5.  **[オプション]** で、 **[セキュリティ情報を含める]** チェック ボックスをオンのままにします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックから復元する場合は、この設定は適用されません。  
  
## <a name="see-also"></a>参照  
 [表形式モデル データベース](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)   
 [Power Pivot からのインポート](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)  
  
  
