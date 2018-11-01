---
title: PolyBase の機能と制限事項 | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2052b098f0be7ab377cf38a36b896794d3caa07a
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874350"
---
# <a name="polybase-features-and-limitations"></a>PolyBase の機能と制限事項

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

SQL Server の製品やサービスで利用可能な PolyBase 機能の概要です。  
  
## <a name="feature-summary-for-product-releases"></a>製品リリースの機能の概要

PolyBase の主な機能と、これらの機能を利用できる製品をまとめた表を次に示します。  
  
||||||
|-|-|-|-|-|   
|**機能**|**SQL Server 2016**|**Azure SQL Database**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|いいえ|いいえ|はい|
|Hadoop からデータをインポートする|はい|いいえ|いいえ|はい|
|データを Hadoop にエクスポートする  |はい|いいえ|いいえ| はい|
|HDInsights のクエリ、インポート、エクスポート |いいえ|いいえ|いいえ|いいえ
|クエリの計算を Hadoop にプッシュダウンする|はい|いいえ|いいえ|はい|  
|Azure blob ストレージからデータをインポートする|はい|いいえ|はい|はい| 
|Azure blob ストレージにデータをエクスポートする|はい|いいえ|はい|はい|  
|Azure Data Lake Store からデータをインポートする|いいえ|いいえ|はい|いいえ|    
|Azure Data Lake Store からデータをエクスポートする|いいえ|いいえ|はい|いいえ|
|Microsoft BI ツールから PolyBase クエリを実行する|はい|いいえ|はい|はい|   

## <a name="pushdown-computation-supported-t-sql-operators"></a>プッシュダウン計算でサポートされる T-SQL 演算子

SQL Server および APS では、すべての T-SQL 演算子を hadoop クラスターにプッシュダウンできるわけではありません。 次の表は、すべてサポートされている演算子と、サポートされていない演算子のサブセットを示しています。 

||||
|-|-|-| 
|**演算子の種類**|**Hadoop にプッシュ可能**|**Blob ストレージにプッシュ可能**|
|列のプロジェクション|はい|いいえ|
|述語|はい|いいえ|
|集計|部分的|いいえ|
|外部テーブル間の結合のみ|いいえ|いいえ|
|外部テーブルとローカル テーブル間の結合|いいえ|いいえ|
|並べ替え|いいえ|いいえ|

部分的な集計は、データが SQL Server に達しても Hadoop で集計の一部が発生した後に、最終的な集計を行う必要があることを意味します。 これは、超並列処理システムで一般的な集計の計算方法です。  

## <a name="known-limitations"></a>既知の制限事項

PolyBase には次の制限事項があります。

- 可変長列の全長を含め、最大行サイズは SQL Server で 32 KB 以下、または Azure SQL Data Warehouse で 1 MB 以下にする必要があります。

- PolyBase では、Hive 0.12 以降のデータ型 (つまり、Char(), VarChar()) はサポートされません。

- SQL Server または Azure SQL データ ウェアハウスから ORC ファイル形式にデータをエクスポートするとき、java のメモリ不足エラーに起因し、テキストでいっぱいの列はわずか 50 列に制限されることがあります。 この問題を回避するには、列の一部だけをエクスポートします。

- Hadoop に保存されている暗号化されたデータの読み取りまたは書き込みができません。 これには、HDFS 暗号化ゾーンまたは透過的な暗号化が含まれます。

- KNOX が有効になっている場合、PolyBase は、Hortonworks インスタンスに接続できません。

- transactional = true の Hive テーブルを使用している場合、PolyBase は Hive テーブルのディレクトリにあるデータにアクセスできません。

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [SQL Server 2016 のフェールオーバー クラスターにノードを追加すると、PolyBase の機能をインストールできません](https://support.microsoft.com/en-us/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster)

::: moniker-end
- 統合認証はサポートされていません。 現在は、ユーザー名とパスワードのみがサポートされています。  
- 暗号化は既定で有効になります。 暗号化を無効にするには、... を行う必要があります (thanh と話す)
- [型マッピングの制限](polybase-type-mapping.md)


## <a name="security-and-authentication"></a>セキュリティと認証 

## <a name="see-also"></a>参照  

[PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)  
