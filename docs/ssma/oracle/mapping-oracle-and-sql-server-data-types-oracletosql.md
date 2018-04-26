---
title: Oracle と SQL Server データ型 (OracleToSQL) マッピング |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Type Mapping Inheritance
ms.assetid: 05da1495-63b9-47b7-86e2-6746394a2d8a
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 14abe4d362eead87d83ab8ea9b9082f8c2c8f566
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="mapping-oracle-and-sql-server-data-types-oracletosql"></a>Oracle と SQL Server データ型 (OracleToSQL) とのマッピング
Oracle データベースの種類が異なる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースの型。 Oracle データベース オブジェクトを変換する際に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト、Oracle からのデータ型にマップする方法を指定する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 既定のデータ型マッピングを受け入れることができますか、マップをカスタマイズするには、次のセクションで示すようにします。  
  
## <a name="default-mappings"></a>既定のマッピング  
SSMA では、データ型マッピングの既定のセットがあります。 既定のマッピングの一覧で、次を参照してください。[プロジェクト設定&#40;型マッピング&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md)です。  
  
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
  
    または、データの種類をカスタマイズするには、データベース、テーブル、ビュー、またはストアド プロシージャ レベルのマッピング データベース、オブジェクトのカテゴリ、またはオブジェクト Oracle メタデータ エクスプ ローラーで選択。  
  
    1.  Oracle メタデータ エクスプ ローラーでフォルダーまたはカスタマイズするオブジェクトを選択します。  
  
    2.  右側のウィンドウでをクリックして、**型マッピング**タブです。  
  
2.  新しいマッピングを追加するには、次の操作を行います。  
  
    1.  **[追加]** をクリックします。  
  
    2.  **ソースの種類**、Oracle データ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合のマッピングの最小限のデータ長の指定、**から**ボックスと 最大データ長、**に**ボックス。  
  
        これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。  
  
    4.  **ターゲット型**、ターゲットを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
        一部の種類では、対象のデータ型の長さが必要です。 必要な場合は、入力で新しいデータの長さ、**置き換えます**ボックス。  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
3.  データ型マッピングを変更するには、次の操作を行います。  
  
    1.  **[編集]** をクリックします。  
  
    2.  **ソースの種類**、Oracle データ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合のマッピングの最小限のデータ長の指定、**から**ボックスと 最大データ長、**に**ボックス。  
  
        これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。  
  
    4.  **ターゲット型**、ターゲットを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
        一部の種類では、対象のデータ型の長さが必要です。 必要な場合は、入力で新しいデータの長さ、**置き換えます**ボックスで、し、 [!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
4.  カスタム データ型マッピングを削除するには、次の操作を行います。  
  
    1.  削除するデータ型のマッピングを含んだ型マッピングの一覧で、行を選択します。  
  
    2.  **[削除]** をクリックします。  
  
        継承されたマッピングを削除することはできません。 ただし、継承されたマッピングは、特定のオブジェクトまたはオブジェクト カテゴリにカスタムへのマッピングによって上書きされます。  
  
## <a name="next-steps"></a>次の手順  
移行プロセスの次の手順は、いずれかに[評価レポートを作成する](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357)または[Oracle データベースのオブジェクトを SQL Server の構文に変換](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272)です。 評価レポートを作成する場合、Oracle オブジェクトは、評価時に自動的に変換されます。  
  
## <a name="see-also"></a>参照  
[SQL Server にデータベースを移行する Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
