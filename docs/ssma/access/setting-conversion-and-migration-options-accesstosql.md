---
title: 変換と移行オプション (AccessToSQL) の設定 |Microsoft Docs
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
- conversion, setting options
- migration options
- modes
- options, conversion settings
- project settings
- schemas
ms.assetid: 0a7304df-2f35-4453-96ef-7ac83dea1167
caps.latest.revision: 20
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 21cbf6f3a5dac0b77669b940bf27be26198a4456
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394769"
---
# <a name="setting-conversion-and-migration-options-accesstosql"></a>変換と移行オプション (AccessToSQL) の設定
SSMA プロジェクトごとに、プロジェクト レベルのオプションを設定することができます。 これらのオプションは、オブジェクトに変換する方法、データを移行する方法、およびソースのデータ型が対象のデータ型にマップする方法を指定します。 オブジェクトを変換する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure にデータを移行または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure、構成オプションが、プロジェクトの適切なことを確認します。  
  
## <a name="configuration-options-and-modes"></a>構成オプションとモード  
SSMA は 4 つのセットの構成設定とこれらの設定を構成するための 4 つのモード: 既定、Optimistic、Full、およびユーザー設定。 ほとんどのユーザーには、既定のモードを使用することをお勧めします。 単純な変換をオプティミスティック モードを使用します。 すべてのメッセージを表示する場合は、完全なモードを使用します。 カスタム モードでは、オプションを設定します。  
  
設定は、このドキュメントの「ユーザー インターフェイス リファレンス」のセクションで説明します。 設定と各モードで、設定を適用する方法の詳細については、次のトピックを参照してください。  
  
-   [プロジェクトの設定 (変換)](http://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
-   [プロジェクトの設定 (移行)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)  
  
-   [プロジェクトの設定 (GUI)](http://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [プロジェクトの設定 (型のマッピング)](http://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655)  
  
-   [プロジェクトの設定 (SQL Azure)](http://msdn.microsoft.com/bbb8a204-d0e4-4f0b-9709-271feb1f136e)  
  
## <a name="setting-project-options"></a>プロジェクト オプションの設定  
SSMA では、すべてのプロジェクトの既定の設定を構成できます。 これらの設定は SSMA の構成ファイルに保存し、作成した新しいプロジェクトに適用します。  
  
**既定のプロジェクトのオプションを設定するには**  
  
1.  **ツール**メニューの **プロジェクト設定の既定の**します。  
  
2.  **プロジェクト設定の既定の** ダイアログ ボックスで、次のいずれかの操作を行います。  
  
    -   設定は、表示/から変更する必要を移行プロジェクトの種類を選択**移行ターゲット バージョン**ドロップダウンで、**全般**を選択し、左側のウィンドウの下部にある**変換または移行または SQL Azure**します。  
  
        > [!NOTE]  
        > SQL Azure のオプションは、**全般**作成されたプロジェクトの種類が SQL Azure の場合にのみタブします。  
  
    -   定義済みのモードを選択する**既定**、 **Optimistic**、または**完全**で、**モード** ボックスの一覧。  
  
    -   カスタム モードを指定するには、次のように選択します。**カスタム**で、**モード**ボックス、左側のウィンドウでオプションを選択、設定または右側のウィンドウで値をクリックし選択するか、新しい設定または値を入力します。  
  
3.  クリックして**OK**設定を保存します。  
  
現在のプロジェクトの設定をカスタマイズすることもできます。 これらの設定は、現在のプロジェクト ファイルに保存されます。  
  
**現在のプロジェクトの設定をカスタマイズするには**  
  
1.  **ツール**メニューの **プロジェクト設定**します。  
  
2.  **プロジェクト設定** ダイアログ ボックスで、次のいずれかの操作を行います。  
  
    -   定義済みのモードを選択する**既定**、 **Optimistic**、または**完全**で、**モード** ボックスの一覧。  
  
    -   カスタム モードを指定するには、次のように選択します。**カスタム**で、**モード**ボックス、左側のウィンドウでオプションを選択、設定または右側のウィンドウで値をクリックし選択するか、新しい設定または値を入力します。  
  
3.  クリックして**OK**設定を保存します。  
  
## <a name="next-steps"></a>次の手順  
移行の次の手順は、プロジェクトのニーズによって異なります。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください[マッピング ソースとターゲットのデータ型。](mapping-source-and-target-data-types-accesstosql.md)  
  
-   ソースとターゲット データベースのマッピングをカスタマイズするを参照してください[マッピング ソースとターゲット データベース。](mapping-source-and-target-databases-accesstosql.md)  
  
-   Access データベース オブジェクトの定義を変換する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure のオブジェクトの定義。 詳細については、次を参照してください[Access データベース オブジェクトの変換。](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
