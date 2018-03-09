---
title: "プロジェクトのオプション (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Configuration Options and Modes
ms.assetid: a324d07d-cfdf-43bd-98a0-acf332c5a4db
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 0022ce5df4791ba3084507810d3490db2c7ae4dd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="setting-project-options-oracletosql"></a>プロジェクト オプションの設定 (OracleToSQL)
SSMA プロジェクトごとにプロジェクト レベルのオプションを設定することができます。 これらのオプションは、オブジェクトへの変換、オブジェクトの読み込み、ユーザー インターフェイスとデータの移行設定を指定します。 オブジェクトを変換する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]にデータを移行または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、構成オプションが、プロジェクトの適切なであることを確認します。  
  
SSMA では、すべてのプロジェクトの既定のオプションを構成できます。 これらのオプションは、作成した新しいプロジェクトに適用されます。 各プロジェクトのオプションをカスタマイズできます。  
  
## <a name="configuration-options-and-modes"></a>構成オプションとモード  
SSMA では、プロジェクトの設定の 5 つのセットがあります。  
  
-   プロジェクト情報  
  
-   [全般] (変換、オブジェクトの読み込みの移行)  
  
-   Synchronization  
  
-   GUI  
  
-   型のマッピング  
  
これらの設定を構成するための 4 つのモードがあります。  
  
-   既定値  
  
-   オプティミスティック  
  
-   [完全]  
  
-   Custom  
  
ほとんどのユーザーには、既定のモードを使用することをお勧めします。 オプティミスティック モードでは、現在の Oracle の構文の詳細を保持しが読みやすくします。 ただし、現在の構文を保持できない可能性があります正確です。 Oracle の構文は、それと同等に変換する必要がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文、フル モードには、最も包括的な変換が実行されますが、結果のコードが読みにくくなる可能性があります。 カスタム モードでは、オプションを設定します。  
  
設定と各モードの設定を適用する方法の詳細については、次のトピックを参照してください。  
  
-   [プロジェクトの設定 &#40;です。変換&#41;&#40; OracleToSQL &#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
-   [プロジェクトの設定 &#40;です。移行&#41;&#40; OracleToSQL &#41;](../../ssma/oracle/project-settings-migration-oracletosql.md)  
  
-   [プロジェクトの設定 &#40;です。同期 &#41;&#40; OracleToSQL &#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md)  
  
-   [プロジェクトの設定 &#40;です。GUI &#41;&#40; OracleToSQL &#41;](../../ssma/oracle/project-settings-gui-oracletosql.md)  
  
-   [プロジェクトの設定 &#40;です。型のマッピング &#41;&#40; OracleToSQL &#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md)  
  
## <a name="setting-project-options"></a>プロジェクト オプションの設定  
SSMA では、すべてのプロジェクトの既定の設定を構成できます。 これらの設定は SSMA 構成ファイルに保存して、作成した新しいプロジェクトに適用します。  
  
**既定のプロジェクトのオプションを設定するには**  
  
1.  **ツール** メニューのをクリックして**プロジェクト設定の既定の**します。  
  
2.  **プロジェクト設定の既定の**ダイアログ ボックスで、次の手順のいずれかを使用します。  
  
    -   設定は表示または変更に必要な移行プロジェクトの種類を選択して**移行のターゲット バージョン**をクリックしてドロップダウン**全般**左側のウィンドウ を選択または変換と移行の下部にあります。  
  
    -   定義済みのモードを選択する、**モード**ドロップダウン ボックスで、**既定**、 **Optimistic**、または**完全**です。  
  
    -   カスタム設定を指定するを選択するか、新しい設定または値を入力します。  
  
3.  をクリックして**OK**設定を保存します。  
  
現在のプロジェクトの設定をカスタマイズすることもできます。 これらの設定は、現在のプロジェクト ファイルに保存されます。  
  
**現在のプロジェクトの設定をカスタマイズするには**  
  
1.  **ツール** メニューのをクリックして**プロジェクト設定**です。  
  
2.  **プロジェクト設定**ダイアログ ボックスで、次の手順のいずれかを使用します。  
  
    -   定義済みのモードを選択する、**モード**ドロップダウン ボックスで、**既定**、 **Optimistic**、または**完全**です。  
  
    -   カスタムのモードを指定する、**モード**ボックスで、**カスタム**、適切なプロジェクト設定を選択します。  
  
3.  をクリックして**OK**設定を保存します。  
  
## <a name="next-steps"></a>Next Steps  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください。[マッピング Oracle と SQL Server データ型 &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)です。  
  
-   それ以外の場合に Oracle データベース オブジェクトの定義を変換できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト定義します。 詳細については、次を参照してください。 [Oracle スキーマを変換する &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)です。  
  
## <a name="see-also"></a>参照  
[マッピング Oracle と SQL Server データ型 &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)  
  
