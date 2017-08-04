---
title: "マッピングの MySQL および SQL Server データ型 (MySQLToSQL) |Microsoft ドキュメント"
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
helpviewer_keywords:
- Mapping, customize data type mapping
- Mapping, Type mapping
ms.assetid: 14f98054-13b4-4231-a6b0-2452f3b9941d
caps.latest.revision: 15
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3dd2adf0b8f6379bd11dc80de4cc2aedf5b3c102
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mapping-mysql-and-sql-server-data-types-mysqltosql"></a>MySQL および SQL Server データ型 (MySQLToSQL) のマッピング
MySQL データベースの種類が異なる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースの種類。 MySQL のデータベース オブジェクトを変換する際に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクトに MySQL からのデータ型にマップする方法を指定する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 既定のデータ型マッピングを受け入れることができますか、マップをカスタマイズするには、次の手順で示すようにします。  
  
## <a name="default-mappings"></a>既定のマッピング  
SSMA では、データ型マッピングの既定のセットがあります。 既定のマッピングの一覧で、次を参照してください。[プロジェクトの設定 & #40 です。型のマッピング &#41;& #40 です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
## <a name="type-mapping-inheritance"></a>型の継承のマッピング  
プロジェクト レベル、オブジェクトのカテゴリ レベル (すべてのストアド プロシージャなど)、またはオブジェクト レベルでは、型マッピングをカスタマイズすることができます。 設定は、下位レベルでオーバーライドされない限りより高いレベルから継承されます。 たとえば、マップする**smallint**に**int**オブジェクトまたはカテゴリ レベルのマッピングをカスタマイズしない限り、このマッピング プロジェクト レベルでは、プロジェクト内のすべてのオブジェクトが使用されます。  
  
表示すると、**型マッピング**SSMA、バック グラウンドのタブが色分けされ、どの型のマッピングは、継承を表示します。 型マッピングの背景は、任意の継承された型のマッピング、および現在のレベルで指定されているすべてのマッピングを白に黄色です。  
  
## <a name="customizing-data-type-mappings"></a>データ型マッピングのカスタマイズ  
  
-   **データ型をマップします。**  
  
    次の手順では、プロジェクト、データベース、またはデータベース オブジェクト レベルでのデータ型にマップする方法を示しています。  
  
    1.  プロジェクト全体のデータ型マッピングをカスタマイズするには、開く、**プロジェクト設定** ダイアログ ボックス。 [ツール] メニューで、次のように選択します。**プロジェクト設定**です。  
  
        左のペインで選択**型マッピング**です。 型マッピングのグラフとボタンは、右側のペインに表示されます。  
  
    2.  データベースまたはテーブル レベルでのデータ型マッピングをカスタマイズするには、MySQL メタデータ エクスプ ローラーで、データベースまたはテーブルを選択します。 MySQL メタデータ エクスプ ローラーでフォルダーまたはカスタマイズするオブジェクトを選択します。  
  
        右側のウィンドウでをクリックして**型マッピング**です。  
  
-   **新しいマッピングを追加するには、次の操作を行います。**  
  
    1.  型マッピングのウィンドウで、をクリックして**追加**です。  
  
    2.  New マッピング ダイアログ ボックスを下にある入力**ソースの種類**MySQL のデータ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合を選択して、マッピングの最小値と最大データ長を指定、**から**と**に**チェック ボックスをオンし、値を入力します。  
  
    4.  これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。 **ターゲット型**対象の SQL Server または SQL Azure のデータの種類を選択します。  
  
        1.  一部の種類では、対象のデータ型の長さが必要です。 必要に応じて、入力で新しいデータの長さ、**置換**ボックスし、をクリックして**[ok]**です。  
  
        2.  一部の種類が対象のデータ型を必要と**精度**と**スケール**です。 必要に応じて、新しい有効桁数を入力しのスケールを**置換**ボックスし、をクリックして**OK**です。  
  
-   **型のマッピングを編集するには、次の操作を行います。**  
  
    1.  型マッピングのウィンドウで、をクリックして**編集**です。  
  
    2.  型マッピングの場合は、ダイアログ ボックスを一覧表示**ソースの種類**MySQL のデータ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合を選択して、マッピングの最小値と最大データ長を指定、**から**と**に**チェック ボックスをオンし、値を入力します。  
  
    これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。 **ターゲット型**対象の SQL Server または SQL Azure のデータの種類を選択します。  
  
    1.  一部の種類では、対象のデータ型の長さが必要です。 必要に応じて、入力で新しいデータの長さ、**置換**ボックスし、をクリックして**[ok]**です。  
  
    2.  一部の種類が対象のデータ型を必要と**精度**と**スケール**です。 必要に応じて、新しい有効桁数を入力しのスケールを**置換**ボックスし、をクリックして**OK**です。  
  
-   **データ型マッピングを削除するには、次の操作を行います。**  
  
    1.  ウィンドウで、型マッピングを削除するデータ型のマッピングを含む型マッピングのリスト内の行を選択します。  
  
    2.  **[削除]**をクリックします。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は、いずれかに[評価レポートを作成する](http://msdn.microsoft.com/en-us/2a56a003-3b0f-453a-963c-00c9e40933ec)または[変換の MySQL データベースのオブジェクトを SQL Server または SQL Azure の構文に](http://msdn.microsoft.com/en-us/ac21850b-fb32-4704-9985-5759b7c688c7)です。 レポートを作成する場合、MySQL オブジェクトは、評価時に自動的に変換されます。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への MySQL データベースの移行MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

