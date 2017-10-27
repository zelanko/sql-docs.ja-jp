---
title: "プロジェクトのオプション (MySQLToSQL) |Microsoft ドキュメント"
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
- Setting project options,configuration options
ms.assetid: 08820d88-e157-4d49-9401-38580dd7ec2d
caps.latest.revision: 12
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 005889e4a4fc813819f6133d7a5a7b2a5223b861
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="setting-project-options-mysqltosql"></a>プロジェクト オプションの設定 (MySQLToSQL)
SSMA プロジェクトごとに、プロジェクト レベルのオプションを設定できます。 これらのオプションは、オブジェクトの変換方法、データの移行方法、および対象のデータ型へのソースのデータ型のマップ方法を指定します。  SQL Server または SQL Azure オブジェクトに変換したり、SQL Server または SQL Azure にデータを移行する前に、構成オプションには、プロジェクトの適切なことを確認します。  
  
SSMA では、すべてのプロジェクトの既定のオプションを構成できます。 これらのオプションは、作成した新しいプロジェクトに適用されます。 各プロジェクトのオプションをカスタマイズできます。  
  
## <a name="configuration-options-and-modes"></a>構成オプションとモード  
SSMA では、プロジェクトの設定の 5 つのセットがあります。  
  
-   プロジェクト情報  
  
-   [全般]\(変換、移行、および SQL Azure)  
  
-   Synchronization  
  
-   GUI  
  
-   型のマッピング  
  
プロジェクトの設定は、次の 4 つの方法で構成できます。  
  
-   既定値  
  
-   オプティミスティック  
  
-   Full  
  
-   Custom  
  
ほとんどのユーザーには、既定のモードを使用することをお勧めします。 オプティミスティック モードでは、現在の MySQL 構文の詳細を保持しが読みやすくします。 ただし、現在の構文を保持できない可能性があります正確です。 MySQL の構文は、同等の SQL Server または SQL Azure の構文に変換する必要があります、フル モードは最も包括的な変換を実行します。 結果のコードでは、ただし、あります読みにくくなります。 カスタム モードでは、オプションを設定できます。  
  
設定と各モードの設定を適用する方法の詳細については、次のトピックを参照してください。  
  
-   [プロジェクトの設定 &#40;です。変換"&"#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
-   [プロジェクトの設定 &#40;です。移行"&"#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md)  
  
-   [プロジェクトの設定 (GUI) (SSMA 共通)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [プロジェクトの設定 &#40;です。型のマッピング &#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md)  
  
-   [プロジェクトの設定 &#40;です。同期 &#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
-   [プロジェクトの設定 &#40;です。Azure SQL DB &#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md)  
  
## <a name="setting-project-options"></a>プロジェクト オプションの設定  
SSMA では、すべてのプロジェクトの既定の設定を構成できます。 これらの設定は SSMA 構成ファイルに保存して、作成した新しいプロジェクトに適用します。  
  
**既定のプロジェクトのオプションを設定するには**  
  
1.  **ツール** メニューのをクリックして**プロジェクト設定の既定の**します。  
  
2.  **プロジェクト設定の既定の**ダイアログ ボックスで、次の手順のいずれかを使用します。  
  
    1.  対象の設定が表示する/から変更を必要な移行プロジェクトの種類を選択**移行のターゲット バージョン**ドロップダウンで、をクリックして**全般**クリックし、左側のウィンドウの下部にある**変換または移行または SQL Azure**オプション。  
  
    2.  定義済みのモードを選択する**既定**、 **Optimistic**、または**完全**から、**モード** ボックスの一覧です。  
  
    3.  カスタム設定を指定するを選択するか、新しい設定または値を入力します。  
  
3.  クリックして **OK** 、設定を保存します。  
  
現在のプロジェクトの設定をカスタマイズすることもできます。 設定は、現在のプロジェクト ファイルに保存されます。  
  
**現在のプロジェクトの設定をカスタマイズするには**  
  
1.  **ツール** メニューのをクリックして**ProjectSettings**です。  
  
2.  **ProjectSettings**ダイアログ ボックスで、次の手順のいずれかを使用します。  
  
    1.  定義済みのモードを選択する**既定**、 **Optimistic**、または**完全**から、**モード** ボックスの一覧です。  
  
    2.  カスタム モードを指定するには、次のように選択します。**カスタム**から、**モード** ボックスの一覧です。 適切なプロジェクト設定を選択します。  
  
3.  クリックして **OK** 、設定を保存します。  
  
## <a name="next-step"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください。[マッピング MySQL および SQL Server データ型 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   それ以外の場合、SQL Server または SQL Azure オブジェクトの定義に、MySQL データベースのオブジェクトの定義を変換できます。 詳細については、次を参照してください。 [MySQL データベースを変換する &#40;です。MySQLToSQL &#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[マッピング MySQL および SQL Server データ型 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  

