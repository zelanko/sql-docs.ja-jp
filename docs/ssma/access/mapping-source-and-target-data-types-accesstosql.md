---
title: "マッピングのソースとターゲットのデータ型 (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- customizing data type mappings
- data types, mapping
- mapping, data types
- source data types
- target data types
ms.assetid: b362a075-16e7-423f-b63f-e1e9f02844a9
caps.latest.revision: "14"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 50bbc2bc214fd0ad8c7e997ea36c1edd0b764421
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mapping-source-and-target-data-types-accesstosql"></a>マップ元と対象のデータ型 (AccessToSQL)
Access データベースの種類が異なる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースの型。 データベース オブジェクトを変換する際に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクトへのアクセスからのデータ型にマップする方法を指定する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 既定のデータ型マッピングを受け入れることができますか、マップをカスタマイズするには、次の手順で示すようにします。  
  
## <a name="default-mappings"></a>既定のマッピング  
SSMA では、データ型マッピングの既定のセットがあります。 既定のマッピングの一覧で、次を参照してください。[プロジェクトの設定 (型のマッピング)](http://msdn.microsoft.com/en-us/b87b9683-abed-4677-8c50-18bdba704655)です。  
  
## <a name="customizing-data-type-mappings"></a>データ型マッピングのカスタマイズ  
使用して、**プロジェクト設定**ダイアログ ボックスで、すべてのデータベースと、プロジェクト内のデータベース オブジェクトの種類をマップする方法をカスタマイズすることができます。 プロジェクトの種類のマッピングは、すべてのデータベースおよびカスタム型マッピングがないデータベース オブジェクトに適用されます。  
  
データベースまたはテーブル レベルでのデータ型マッピングをカスタマイズすることもできます。  
  
次の手順では、プロジェクト、データベース、またはデータベース オブジェクト レベルでのデータ型にマップする方法を示します。  
  
**データ型をマップするには**  
  
1.  プロジェクト全体のデータ型マッピングをカスタマイズするには、開く、**プロジェクト設定** ダイアログ ボックス。  
  
    1.  **ツール**メニューの **プロジェクト設定**です。  
  
    2.  左のペインで選択**型マッピング**です。  
  
        型マッピングのグラフとボタンは、右側のペインに表示されます。  
  
    または、データベースまたはテーブル レベルでのデータ型マッピングをカスタマイズするアクセス メタデータ エクスプ ローラー ペインで、データベースまたはテーブルを選択します。  
  
    1.  アクセス メタデータ エクスプ ローラー] ウィンドウで [**アクセス メタベース**の順に展開および**データベース**です。  
  
    2.  データ型のマッピングをカスタマイズする、データベースまたはテーブルを選択します。  
  
    3.  右側のウィンドウでをクリックして**型マッピング**です。  
  
2.  新しいマッピングを追加するには、次の操作を行います。  
  
    1.  型マッピングのウィンドウで、をクリックして**追加**です。  
  
    2.  **新しい種類のマッピング**ダイアログ ボックスで、**ソースの種類**アクセスのデータ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合を選択して、マッピングの最小値と最大データ長を指定、**から**と**に**チェック ボックスをオンし、値を入力します。  
  
        これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。  
  
    4.  **ターゲット型**、ターゲットを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
        一部の種類では、対象のデータ型の長さが必要です。 必要な場合で新しいデータの長さを入力してください、**置換後の文字列**ボックスし、をクリックして**OK**です。  
  
3.  データ型マッピングを編集するには、次の操作を行います。  
  
    1.  型マッピングのウィンドウで、をクリックして**編集**です。  
  
    2.  **型マッピング リスト**ダイアログ ボックスで、**ソースの種類**アクセスのデータ型にマップを選択します。  
  
    3.  型には、長さが必要とする場合を選択して、マッピングの最小値と最大データ長を指定、**から**と**に**チェック ボックスをオンし、値を入力します。  
  
        これにより、同じデータ型の値より小さいとより大きな値のデータ マッピングをカスタマイズできます。  
  
    4.  **ターゲット型**、ターゲットを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
        一部の種類では、対象のデータ型の長さが必要です。 必要な場合で新しいデータの長さを入力してください、**置換後の文字列**ボックスし、をクリックして**OK**です。  
  
4.  データ型マッピングを削除するには、次の操作を行います。  
  
    1.  ウィンドウで、型マッピングを削除するデータ型のマッピングを含む型マッピングのリスト内の行を選択します。  
  
    2.  **[削除]**をクリックします。  
  
## <a name="next-steps"></a>次の手順  
移行プロセスの次の手順は[データベース オブジェクトへのアクセスを SQL Server オブジェクトに変換します。](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
