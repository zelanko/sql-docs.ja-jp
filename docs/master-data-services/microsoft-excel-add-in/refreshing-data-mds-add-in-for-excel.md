---
title: "データの更新 (Excel 用 MDS アドイン) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58dbe99a-288d-4f1c-9cd5-704d6836c945
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# データの更新 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] では、MDS リポジトリから最新の情報を取得する必要があるときに、新しいワークシートを開くことなくデータを更新できます。 すべてのセルを更新することも、選択したセルだけを更新することもできます。 これは、カスタム式や MDS で管理されないその他のデータを含む列を挿入し、そのデータを保存する必要がある場合に便利です。  
  
## MDS によって管理されるデータを更新できる場合  
 アクティブなワークシートに MDS によって管理されるデータが既に含まれている場合、アクティブなワークシート内の MDS によって管理されるデータを更新できます。 属性値を変更した場合や、メンバーをワークシートに追加した場合は、更新する前に変更をパブリッシュする必要があります。  
  
## 選択範囲の更新  
 すべてのセルを更新するか、選択したセルだけを更新するかを選択できます。 選択するセルは連続している必要があります。 連続した一連のセルが選択されると、そのセット内にある MDS によって管理されるセルは、サーバー上に現在格納されている値を表示するために更新されます。 MDS によって管理されていない未変更の行および列は、まったく影響を受けません。  
  
## MDS によって管理されるデータを更新したときの処理  
 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] でデータを更新したときに、シート内の MDS によって管理されるデータがどのように処理されるかは、データを最後に読み込んだ後に MDS リポジトリで行った変更の内容によります。  
  
-   新しいメンバーをリポジトリに追加した場合は、そのメンバーがワークシートの末尾に追加され、緑色で強調表示されます。  
  
-   リポジトリからメンバーを削除した場合は、そのメンバーがワークシートから削除されます。  
  
-   MDS リポジトリで属性値を変更した場合は、MDS リポジトリのその値を使用して、ワークシート内の値が更新されます。 セルの色は変化しません。  
  
> [!WARNING]  
>  -   アクティブなワークシートで、MDS によって管理されるデータ下の行に管理されないデータが存在する場合、管理されないデータが上書きされることがあります。 これは、シートを更新して、管理されないデータと重複する、MDS によって管理されるデータの新しい行を追加した場合に発生します。  
> -   更新すると、MDS によって管理されるセルのコメントは削除されます。  
  
## MDS によって管理されるデータを更新する方法  
 リボンの **[接続と読み込み]** グループの **[更新]** ボタンには、**[すべて更新]** と **[選択範囲を更新]** の 2 つのオプションがあります。 このリボン ボタンの既定アクションは、**[すべて更新]** です。 シート全体をサーバーの値に更新するには、**[更新]** ボタンをクリックするか、**[すべて更新]** オプションを選択します。 シート内のいくつかのセルのみを更新するには、該当するセルを選択し (1 つの連続する範囲である必要があります)、**[選択範囲を更新]** オプションを選択します。  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースへの接続を作成します。|[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|MDS データを Excel に読み込みます。|[マスター データ サービスから Excel へのデータのエクスポート](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
  
## 関連コンテンツ  
  
-   [接続 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [概要: Excel へのデータのエクスポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Microsoft Excel 用マスター データ サービス アドイン](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  