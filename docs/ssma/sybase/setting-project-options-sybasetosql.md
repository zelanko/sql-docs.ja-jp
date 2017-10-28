---
title: "プロジェクトのオプション (SybaseToSQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- Project Options Setting
ms.assetid: 97b70fc8-1f68-4f15-8e22-db5b784ea4ec
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 40c2bffdb58fadfa3a9c7da58cf68b8c4390cd16
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="setting-project-options-sybasetosql"></a>プロジェクト オプションの設定 (SybaseToSQL)
SSMA プロジェクトごとに、プロジェクト レベルのオプションを設定することができます。 これらのオプションは、オブジェクトへの変換、オブジェクトの読み込み中、SQL azure、ユーザー インターフェイス、およびデータ移行の設定を指定します。 オブジェクトを変換する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure にデータを移行または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、設定オプションが、プロジェクトの適切なであることを確認します。  
  
SSMA では、すべてのプロジェクトの既定のオプションを構成できます。 これらのオプションは、作成する新しいプロジェクトに適用されます。 各プロジェクトのオプションをカスタマイズできます。  
  
## <a name="configuration-options-and-modes"></a>構成オプションとモード  
SSMA では、プロジェクトの設定の 5 つのセットがあります。  
  
1.  プロジェクト情報  
  
2.  [全般]\ (変換、移行とデータの収集)  
  
3.  Synchronization  
  
4.  GUI  
  
5.  型のマッピング  
  
これらの設定を構成するための 4 つのモードがあります。  
  
1.  既定値  
  
2.  オプティミスティック  
  
3.  Full  
  
4.  Custom  
  
ほとんどのユーザーには、既定のモードを使用することをお勧めします。 オプティミスティック モードでは、Sybase Adaptive Server Enterprise (ASE) の現在の構文の詳細を保持し、読みやすきます。 ただし、現在の構文を保持できない可能性があります正確です。 ASE 構文は、それと同等に変換する必要がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の構文、フル モードには、完了、変換が実行されますが、結果のコードが読みにくくなる可能性があります。 カスタム モードでは、オプションを設定します。  
  
設定は、このドキュメントのユーザー インターフェイス リファレンスのセクションで説明します。 設定と各モードの設定を適用する方法の詳細については、次のトピックを参照してください。  
  
-   [プロジェクトの設定 &#40;です。変換&#41; &#40;です。SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
-   [プロジェクトの設定 &#40;です。移行&#41; &#40;です。SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md)  
  
-   [プロジェクトの設定 &#40;です。同期&#41; &#40;です。SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md)  
  
-   [プロジェクトの設定 &#40;です。GUI&#41; &#40;です。SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md)  
  
-   [プロジェクトの設定 &#40;です。型のマッピング&#41; &#40;です。SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)  
  
-   [プロジェクトの設定 &#40;です。Azure SQL DB&#41; &#40;です。SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md)  
  
## <a name="setting-project-options"></a>プロジェクト オプションの設定  
SSMA では、すべてのプロジェクトの既定の設定を構成できます。 これらの設定は SSMA 構成ファイルに保存して、作成した新しいプロジェクトに適用します。  
  
**既定のプロジェクトのオプションを設定するには**  
  
1.  **ツール**メニューの **プロジェクト設定の既定の**します。  
  
2.  **プロジェクト設定の既定の**ダイアログ ボックスで、次の手順のいずれかを使用します。  
  
    -   設定は表示または変更に必要な移行プロジェクトの種類を選択**移行のターゲット バージョン**ドロップ ダウン左側のウィンドウの下部にある [全般] をクリックし、変換または移行または SQL Azure を選択します。  
  
    -   定義済みのモードを選択する、**モード**ドロップダウン ボックスで、**既定**、 **Optimistic**、または**完全**です。  
  
    -   カスタム設定を指定するには、オンまたは、新しい設定または値を入力します。  
  
3.  クリックして **OK** 、設定を保存します。  
  
現在のプロジェクトの設定をカスタマイズすることもできます。 これらの設定は、現在のプロジェクト ファイルに保存されます。  
  
**現在のプロジェクトの設定をカスタマイズするには**  
  
1.  **ツール**メニューの **プロジェクト設定**です。  
  
2.  **プロジェクト設定**ダイアログ ボックスで、次の手順のいずれかを使用します。  
  
    -   定義済みのモードを選択する、**モード**ドロップダウン ボックスで、**既定**、 **Optimistic**、または**完全**です。  
  
    -   カスタムのモードを指定する、**モード**ドロップダウン ボックスで、**カスタム**、左ペインでオプションを選択、設定または右側のウィンドウで値をクリックし、選択するか、新しい設定または値を入力します。  
  
3.  クリックして **OK** 、設定を保存します。  
  
## <a name="next-steps"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   カスタム ソースとターゲットのデータ型のマッピングを参照してください[マッピング Sybase ASE と SQL Server データ型 &#40;です。SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   それ以外の場合、Sybase データベース オブジェクトの定義を変換できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクトの定義。 詳細については、次を参照してください。 [Sybase ASE データベース オブジェクトの変換 &#40;です。SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40;への Sybase ASE データベースの移行SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

