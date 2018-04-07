---
title: プロジェクトのオプション (DB2ToSQL) |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f325a606-97ac-48bc-b344-b55f5e086a48
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2688a05f0875bc279d993c500a48ca7b6d9f4894
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="setting-project-options-db2tosql"></a>プロジェクト オプションの設定 (DB2ToSQL)
SSMA プロジェクトごとにプロジェクト レベルのオプションを設定することができます。 これらのオプションは、オブジェクトへの変換、オブジェクトの読み込み、ユーザー インターフェイスとデータの移行設定を指定します。 オブジェクトを変換する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]にデータを移行または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、構成オプションが、プロジェクトの適切なであることを確認します。  
  
SSMA では、すべてのプロジェクトの既定のオプションを構成できます。 これらのオプションは、作成した新しいプロジェクトに適用されます。 各プロジェクトのオプションをカスタマイズできます。  
  
## <a name="configuration-options-and-modes"></a>構成オプションとモード  
SSMA では、プロジェクトの設定の 5 つのセットがあります。  
  
-   プロジェクト情報  
  
-   [全般]\(変換、オブジェクトの読み込みの移行)  
  
-   Synchronization  
  
-   GUI  
  
-   型のマッピング  
  
これらの設定を構成するための 4 つのモードがあります。  
  
-   既定値  
  
-   オプティミスティック  
  
-   Full  
  
-   Custom  
  
ほとんどのユーザーには、既定のモードを使用することをお勧めします。 オプティミスティック モードでは、DB2 の現在の構文の詳細を保持し、読みやすきます。 ただし、現在の構文を保持できない可能性があります正確です。 DB2 構文は、それと同等に変換する必要がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文、フル モードには、最も包括的な変換が実行されますが、結果のコードが読みにくくなる可能性があります。 カスタム モードでは、オプションを設定します。  
  
設定と各モードの設定を適用する方法の詳細については、次のトピックを参照してください。  
  
-   [プロジェクトの設定 &#40;です。変換&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)  
  
-   [プロジェクトの設定 &#40;です。移行&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md)  
  
-   [プロジェクトの設定 &#40;です。同期&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)  
  
-   [プロジェクトの設定 &#40;です。GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md)  
  
-   [プロジェクトの設定 &#40;です。型のマッピング&#41; &#40; DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)  
  
## <a name="setting-project-options"></a>プロジェクト オプションの設定  
SSMA では、すべてのプロジェクトの既定の設定を構成できます。 これらの設定は SSMA 構成ファイルに保存して、作成した新しいプロジェクトに適用します。  
  
**既定のプロジェクトのオプションを設定するには**  
  
1.  **ツール** メニューのをクリックして**プロジェクト設定の既定の**します。  
  
2.  **プロジェクト設定の既定の**ダイアログ ボックスで、次の手順のいずれかを使用します。  
  
    -   設定は表示または変更に必要な移行プロジェクトの種類を選択して**移行のターゲット バージョン**をクリックしてドロップダウン**全般**左側のウィンドウ を選択または変換と移行の下部にあります。  
  
    -   定義済みのモードを選択する、**モード**ドロップダウン ボックスで、**既定**、 **Optimistic**、または**完全**です。  
  
    -   カスタム設定を指定するを選択するか、新しい設定または値を入力します。  
  
3.  クリックして **OK** 、設定を保存します。  
  
現在のプロジェクトの設定をカスタマイズすることもできます。 これらの設定は、現在のプロジェクト ファイルに保存されます。  
  
**現在のプロジェクトの設定をカスタマイズするには**  
  
1.  **ツール** メニューのをクリックして**プロジェクト設定**です。  
  
2.  **プロジェクト設定**ダイアログ ボックスで、次の手順のいずれかを使用します。  
  
    -   定義済みのモードを選択する、**モード**ドロップダウン ボックスで、**既定**、 **Optimistic**、または**完全**です。  
  
    -   カスタムのモードを指定する、**モード**ボックスで、**カスタム**、適切なプロジェクト設定を選択します。  
  
3.  クリックして **OK** 、設定を保存します。  
  
## <a name="next-steps"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください。[マッピング DB2 と SQL Server データ型 &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)です。  
  
-   それ以外の場合、DB2 データベース オブジェクトの定義を変換できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト定義します。 詳細については、次を参照してください。 [DB2 スキーマを変換する &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md)です。  
  
## <a name="see-also"></a>参照  
[マッピング DB2 と SQL Server データ型 &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)  
  
