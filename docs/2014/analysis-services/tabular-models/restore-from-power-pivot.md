---
title: PowerPivot からの復元 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
author: minewiskan
ms.author: owend
ms.openlocfilehash: b153dfbe9dfdbb5741304153bd7b3dfd1d0d1b3c
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938673"
---
# <a name="restore-from-powerpivot"></a>PowerPivot から復元
  SQL Server Management Studio の PowerPivot から復元機能を使って、テーブル モードで実行されている Analysis Services インスタンス上に新しいテーブル モデル データベースを作成したり、PowerPivot ブック (.xlsx) から既存のデータベースに復元したりできます。  
  
> [!NOTE]  
>  SQL Server Data Tools の PowerPivot からのインポート プロジェクト テンプレートが同様の機能を提供します。 詳細については、「 [PowerPivot からのインポート &#40;SSAS 表形式&#41;](import-from-power-pivot-ssas-tabular.md)」を参照してください。  
  
 PowerPivot から復元機能を使用する場合、次の点に注意してください。  
  
-   PowerPivot から復元機能を使用するには、サーバー管理者ロールのメンバーとして Analysis Services インスタンスにログオンしている必要があります。  
  
-   Analysis Services インスタンス サービス アカウントには、復元するブック ファイルの読み取り権限が必要です。  
  
-   既定では、PowerPivot からデータベースを復元する場合は、テーブル モデル データベースのデータ ソースの権限借用情報プロパティは既定値に設定されており、Analysis Services インスタンス サービス アカウントを指定します。 権限借用の資格情報をデータベース プロパティの Windows ユーザー アカウントに変更することをお勧めします。 詳細については、「[権限借用 (SSAS テーブル)](impersonation-ssas-tabular.md)」を参照してください。  
  
-   PowerPivot データ モデルのデータは、Analysis Services インスタンス上の既存または新規のテーブル モデル データベースにコピーされます。 PowerPivot ブックにリンク テーブルが含まれている場合は、新規テーブルを使用して作成されたテーブルのように、データ ソースを使用せずにテーブルとして再作成されます。  
  
### <a name="to-restore-from-powerpivot"></a>PowerPivot から復元するには  
  
1.  SSMS で、復元先の Active Directory インスタンスの [**データベース**] を右クリックし、[ **PowerPivot から復元**] をクリックします。  
  
2.  [ **PowerPivot から復元**] ダイアログボックスの [**復元元**] の [**バックアップファイル**] で、[**参照**] をクリックし、復元元の abf または .xslx ファイルを選択します。  
  
3.  **[復元対象]** の **[データベースの復元]** で、新しいデータベースまたは既存のデータベースの名前を入力します。 名前を指定しない場合は、ブック名が使用されます。  
  
4.  **[ストレージの場所]** で、 **[参照]** をクリックし、データベースを格納する場所を選択します。  
  
5.  **[オプション]** で、 **[セキュリティ情報を含める]** チェック ボックスをオンのままにします。 PowerPivot ブックから復元する場合は、この設定は適用されません。  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;&#40;テーブルモデルデータベース](tabular-model-databases-ssas-tabular.md)   
 [PowerPivot からのインポート &#40;SSAS 表形式&#41;](import-from-power-pivot-ssas-tabular.md)  
  
  
