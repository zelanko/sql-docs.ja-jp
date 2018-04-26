---
title: マッピング Sybase ASE と SQL Server データ型 (SybaseToSQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Mapping Sybase ASE Schemas to SQL Server Schemas
- Type Mapping Settings
ms.assetid: 784365d3-df4e-47ab-8ee0-d8392b52f510
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cca6fecaee64c828d94bb8f72c3caf2aae3273b6
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="mapping-sybase-ase-and-sql-server-data-types-sybasetosql"></a>Sybase ASE と SQL Server データ型 (SybaseToSQL) とのマッピング
Sybase Adaptive Server Enterprise (ASE) データベースの種類が異なる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースの種類。 ASE 使用するデータベース オブジェクトを変換する際に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクトに ASE からのデータ型にマップする方法を指定する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 既定のデータ型マッピングを受け入れることができますか、マップをカスタマイズするには、次のセクションで示すようにします。  
  
## <a name="default-mappings"></a>既定のマッピング  
SSMA では、データ型マッピングの既定のセットがあります。 既定のマッピングの一覧で、次を参照してください。[プロジェクト設定&#40;型マッピング&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)です。  
  
## <a name="type-mapping-inheritance"></a>型の継承のマッピング  
プロジェクト レベル、オブジェクトのカテゴリ レベル (すべてのストアド プロシージャなど)、またはオブジェクト レベルでは、型マッピングをカスタマイズすることができます。 設定は、下位レベルでオーバーライドされない限りより高いレベルから継承されます。 たとえば、マップする**smallmoney**に**money**カテゴリ レベルのオブジェクトまたはオブジェクト レベルでのマッピングをカスタマイズしない限り、このマッピング プロジェクト レベルでは、プロジェクト内のすべてのオブジェクトが使用されます。  
  
表示すると、**型マッピング**SSMA、バック グラウンドのタブが色分けされ、どの型のマッピングは、継承を表示します。 型マッピングの背景は、任意の継承された型のマッピング、および現在のレベルで指定されたすべてのマッピングを白に黄色です。  
  
## <a name="customizing-data-type-mappings"></a>データ型マッピングのカスタマイズ  
次の手順では、プロジェクト、データベース、またはオブジェクト レベルでのデータ型をマップする方法を示します。  
  
**データ型をマップするには**  
  
1.  プロジェクト全体のデータ型マッピングをカスタマイズするには、開く、**プロジェクト設定** ダイアログ ボックス。  
  
    1.  **ツール**メニューの **プロジェクト設定**です。  
  
    2.  左のペインで選択**型マッピング**です。  
  
        型マッピングのグラフとボタンは、右側のペインに表示されます。  
  
    または、データの種類をカスタマイズするには、データベース、テーブル、ビュー、またはストアド プロシージャ レベルのマッピング データベース、オブジェクトのカテゴリ、またはオブジェクト Sybase メタデータ エクスプ ローラーで選択。  
  
    1.  Sybase メタデータ エクスプ ローラーでフォルダーまたはカスタマイズするオブジェクトを選択します。  
  
    2.  右側のウィンドウでをクリックして、**型マッピング**タブです。  
  
2.  新しいマッピングを追加するには、次の操作を行います。  
  
    1.  **[追加]** をクリックします。  
  
    2.  **ソースの種類**、ASE データ型にマップを選択します。  
  
    3.  内でマッピングの最小限のデータ長の指定の型には、長さが必要とする場合、**から**ボックス、および内でマッピングの最大データ長の指定、**に**ボックス。  
  
        これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。  
  
    4.  **ターゲット型**、ターゲットを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のデータ型。  
  
        一部の種類では、対象のデータ型の長さが必要です。 必要な場合は、入力で新しいデータの長さ、**置き換えます**ボックス。  
  
    5.  **[OK]** をクリックします。  
  
3.  データ型マッピングを編集するには、次の操作を行います。  
  
    1.  **[編集]** をクリックします。  
  
    2.  **ソースの種類**、ASE データ型にマップを選択します。  
  
    3.  内でマッピングの最小限のデータ長の指定の型には、長さが必要とする場合、**から**ボックス、および内でマッピングの最大データ長の指定、**に**ボックス。  
  
        これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。  
  
    4.  **ターゲット型**、ターゲットを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のデータ型。  
  
        一部の種類では、対象のデータ型の長さが必要です。 必要な場合で新しいデータの長さを入力してください、**で置き換えます**ボックスし、をクリックして**OK**です。  
  
4.  カスタム データ型マッピングを削除するには、次の操作を行います。  
  
    1.  削除するデータ型のマッピングを含んだ型マッピングの一覧で、行を選択します。  
  
    2.  **[削除]** をクリックします。  
  
        継承されたマッピングを削除することはできません。 ただし、継承されたマッピングは、特定のオブジェクトまたはオブジェクト カテゴリにカスタムへのマッピングによって上書きされます。  
  
## <a name="next-steps"></a>次の手順  
移行プロセスの次の手順は、いずれかに[評価レポートを作成する](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c)または[変換 Sybase ASE データベース オブジェクトは、SQL Server または SQL Azure の構文を](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3)です。 評価レポートを作成する場合、Sybase ASE オブジェクトは、評価時に自動的に変換されます。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40;への Sybase ASE データベースの移行SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
