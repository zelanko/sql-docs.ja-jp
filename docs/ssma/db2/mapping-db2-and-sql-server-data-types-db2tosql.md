---
title: "マッピング DB2 と SQL Server データ型 (DB2ToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e7e939a8-5e76-4509-beaf-5acd1cab505e
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 18ee9dc4b0e646b4eb6bd374af55c1ac0f98bf4b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mapping-db2-and-sql-server-data-types-db2tosql"></a>DB2 と SQL Server データ型 (DB2ToSQL) とのマッピング
DB2 データベースの種類が異なる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースの型。 DB2 データベース オブジェクトを変換する際に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト、DB2 からのデータ型にマップする方法を指定する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 既定のデータ型マッピングを受け入れることができますか、マップをカスタマイズするには、次のセクションで示すようにします。  
  
## <a name="default-mappings"></a>既定のマッピング  
SSMA では、データ型マッピングの既定のセットがあります。 既定のマッピングの一覧で、次を参照してください。[プロジェクトの設定 & #40 です。型のマッピング &#41;&#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md).  
  
## <a name="type-mapping-inheritance"></a>型の継承のマッピング  
プロジェクト レベル、オブジェクトのカテゴリ レベル (すべてのストアド プロシージャなど)、またはオブジェクト レベルでは、型マッピングをカスタマイズすることができます。 設定は、下位レベルでオーバーライドされない限りより高いレベルから継承されます。 たとえば、マップする**smallmoney**に**money**オブジェクトまたはカテゴリ レベルのマッピングをカスタマイズしない限り、このマッピング プロジェクト レベルでは、プロジェクト内のすべてのオブジェクトが使用されます。  
  
表示すると、**型マッピング**SSMA、バック グラウンドのタブが色分けされ、どの型のマッピングは、継承を表示します。 型マッピングの背景は、任意の継承された型のマッピング、および現在のレベルで指定されているすべてのマッピングを白に黄色です。  
  
## <a name="customizing-data-type-mappings"></a>データ型マッピングのカスタマイズ  
次の手順は、プロジェクト、データベース、またはオブジェクト レベルでのデータ型にマップする方法を示しています。  
  
**データ型をマップするには**  
  
1.  プロジェクト全体のデータ型マッピングをカスタマイズするには、開く、**プロジェクト設定** ダイアログ ボックス。  
  
    1.  **ツール**メニューの **プロジェクト設定**です。  
  
    2.  左のペインで選択**型マッピング**です。  
  
        型マッピングのグラフとボタンは、右側のペインに表示されます。  
  
    または、データの種類をカスタマイズするには、データベース、テーブル、ビュー、またはストアド プロシージャ レベルのマッピング データベース、オブジェクトのカテゴリ、またはオブジェクト DB2 メタデータ エクスプ ローラーで選択。  
  
    1.  DB2 メタデータ エクスプ ローラーでフォルダーまたはカスタマイズするオブジェクトを選択します。  
  
    2.  右側のウィンドウでをクリックして、**型マッピング**タブです。  
  
2.  新しいマッピングを追加するには、次の操作を行います。  
  
    1.  **[追加]**をクリックします。  
  
    2.  **ソースの種類**、DB2 データ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合のマッピングの最小限のデータ長の指定、**から**ボックスと 最大データ長、**に**ボックス。  
  
        これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。  
  
    4.  **ターゲット型**、ターゲットを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
        一部の種類では、対象のデータ型の長さが必要です。 必要な場合は、入力で新しいデータの長さ、**置き換えます**ボックス。  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
3.  データ型マッピングを変更するには、次の操作を行います。  
  
    1.  **[編集]**をクリックします。  
  
    2.  **ソースの種類**、DB2 データ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合のマッピングの最小限のデータ長の指定、**から**ボックスと 最大データ長、**に**ボックス。  
  
        これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。  
  
    4.  **ターゲット型**、ターゲットを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
        一部の種類では、対象のデータ型の長さが必要です。 必要な場合は、入力で新しいデータの長さ、**置き換えます**ボックスで、し、[!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
4.  カスタム データ型マッピングを削除するには、次の操作を行います。  
  
    1.  削除するデータ型のマッピングを含んだ型マッピングの一覧で、行を選択します。  
  
    2.  **[削除]**をクリックします。  
  
        継承されたマッピングを削除することはできません。 ただし、継承されたマッピングは、特定のオブジェクトまたはオブジェクト カテゴリにカスタムへのマッピングによって上書きされます。  
  
## <a name="next-steps"></a>次の手順  
移行プロセスの次の手順は、いずれかに[評価レポート &#40;DB2ToSQL"&"#41;](../../ssma/db2/assessment-report-db2tosql.md)または[DB2 スキーマを変換する &#40;DB2ToSQL"&"#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md)です。 評価レポートを作成する場合、DB2 オブジェクトは、評価時に自動的に変換されます。  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;DB2ToSQL"&"#41; への DB2 データベースの移行](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  

