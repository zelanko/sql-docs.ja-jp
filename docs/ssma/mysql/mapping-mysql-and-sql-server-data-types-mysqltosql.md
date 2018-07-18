---
title: MySQL と SQL Server データ型 (MySQLToSQL) のマッピング |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Mapping, customize data type mapping
- Mapping, Type mapping
ms.assetid: 14f98054-13b4-4231-a6b0-2452f3b9941d
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4690c8db938d53dd290ce642a7fa4ae3884b2a29
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982564"
---
# <a name="mapping-mysql-and-sql-server-data-types-mysqltosql"></a>MySQL と SQL Server データ型 (MySQLToSQL) のマッピング
MySQL データベースの型が異なる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースの型。 MySQL のデータベース オブジェクトを変換する際に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のオブジェクトから MySQL へのデータ型をマップする方法を指定する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 既定のデータ型マッピングをそのまま使用できるまたはマッピングをカスタマイズするには、次の手順で示すようにします。  
  
## <a name="default-mappings"></a>既定のマッピング  
SSMA では、データ型マッピングの既定セットがあります。 既定のマッピングの一覧で、次を参照してください。[プロジェクト設定&#40;型マッピングの&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md)します。  
  
## <a name="type-mapping-inheritance"></a>継承のマッピングの種類  
プロジェクト レベル、オブジェクトのカテゴリ レベル (などすべてストアド プロシージャの場合)、またはオブジェクト レベルでは、型マッピングをカスタマイズすることができます。 設定は、下位のレベルでオーバーライドされない限りより高いレベルから継承されます。 たとえば、マップする**smallint**に**int**オブジェクトまたはカテゴリ レベルでマッピングをカスタマイズしない限り、このマッピング プロジェクト レベルでは、プロジェクト内のすべてのオブジェクトが使用されます。  
  
表示すると、**型マッピングの**SSMA、バック グラウンドのタブが色分けされ、どの型のマッピングは、継承を表示します。 型マッピングの背景は、継承された型のマッピング、および現在のレベルで指定されているすべてのマッピングのホワイト黄色です。  
  
## <a name="customizing-data-type-mappings"></a>データ型マッピングのカスタマイズ  
  
-   **データ型をマップします。**  
  
    次の手順では、プロジェクト、データベース、またはデータベース オブジェクトのレベルでのデータ型にマップする方法を示しています。  
  
    1.  プロジェクト全体のデータ型マッピングをカスタマイズするには、開く、**プロジェクト設定** ダイアログ ボックス。 [ツール] メニューで、次のように選択します。**プロジェクト設定**します。  
  
        左側のウィンドウで次のように選択します。**型マッピングの**します。 右側のウィンドウでは、型マッピングの表とボタンが表示されます。  
  
    2.  データベースまたはテーブル レベルでのデータ型マッピングをカスタマイズするには、MySQL の メタデータ エクスプ ローラーで、データベースまたはテーブルを選択します。 MySQL メタデータ エクスプ ローラーでフォルダーまたはカスタマイズするオブジェクトを選択します。  
  
        右側のウィンドウで次のようにクリックします。**型マッピングの**します。  
  
-   **新しいマッピングを追加するには、次の操作を行います。**  
  
    1.  型マッピングのウィンドウで次のようにクリックします。**追加**します。  
  
    2.  [新しい入力マッピング] ダイアログ ボックスで、**ソースの種類**MySQL のデータ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合は、選択して、マッピングの最小および最大データ長を指定、**から**と**に**チェック ボックスとし、値を入力します。  
  
    4.  これにより、同じデータ型の値が小さくなりより大きなデータのマッピングをカスタマイズできます。 **ターゲットの種類**、ターゲット SQL Server または SQL Azure のデータ型を選択します。  
  
        1.  一部の種類には、対象のデータ型の長さが必要です。 必要に応じて、入力内の新しいデータ長、**置換**ボックスをクリックして **[ok]**。  
  
        2.  一部の種類が対象のデータ型を必要と**精度**と**スケール**します。 必要に応じて、新しい有効桁数を入力し、スケールイン、**置換**ボックスをクリックして**OK**。  
  
-   **型のマッピングを編集するには、次の操作を行います。**  
  
    1.  型マッピングのウィンドウで次のようにクリックします。**編集**します。  
  
    2.  [一覧] ダイアログ ボックスでは、型のマッピングで**ソースの種類**MySQL のデータ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合は、選択して、マッピングの最小および最大データ長を指定、**から**と**に**チェック ボックスとし、値を入力します。  
  
    これにより、同じデータ型の値が小さくなりより大きなデータのマッピングをカスタマイズできます。 **ターゲットの種類**、ターゲット SQL Server または SQL Azure のデータ型を選択します。  
  
    1.  一部の種類には、対象のデータ型の長さが必要です。 必要に応じて、入力内の新しいデータ長、**置換**ボックスをクリックして **[ok]**。  
  
    2.  一部の種類が対象のデータ型を必要と**精度**と**スケール**します。 必要に応じて、新しい有効桁数を入力し、スケールイン、**置換**ボックスをクリックして**OK** 。  
  
-   **データ型のマッピングを削除するには、次の操作を行います。**  
  
    1.  型のマッピング ペインで削除するデータ型マッピングを格納する型マッピングのリスト内の行を選択します。  
  
    2.  **[削除]** をクリックします。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は、いずれかに[評価レポートを作成する](http://msdn.microsoft.com/2a56a003-3b0f-453a-963c-00c9e40933ec)または[変換の MySQL データベースのオブジェクトを SQL Server または SQL Azure の構文に](http://msdn.microsoft.com/ac21850b-fb32-4704-9985-5759b7c688c7)します。 レポートを作成する場合、MySQL のオブジェクトは、評価時に自動的に変換されます。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB への移行 MySQL データベース&#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
