---
title: 変換オプションと移行オプションの設定 (アップグレード)Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- conversion, setting options
- migration options
- modes
- options, conversion settings
- project settings
- schemas
ms.assetid: 0a7304df-2f35-4453-96ef-7ac83dea1167
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 3e89cfd6768aeedd970889cbaea46bb3e1ceae4f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68051498"
---
# <a name="setting-conversion-and-migration-options-accesstosql"></a>変換オプションと移行オプションの設定 (アップグレード)
SSMA プロジェクトごとに、プロジェクトレベルのオプションを設定できます。 これらのオプションでは、オブジェクトの変換方法、データの移行方法、およびソースデータ型とターゲットデータ型のマッピング方法を指定します。 オブジェクトをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換したり、データ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を SQL Azure または SQL Azure に移行したりする前に、構成オプションがプロジェクトに適していることを確認してください。  
  
## <a name="configuration-options-and-modes"></a>構成オプションとモード  
SSMA には、4セットの構成設定と4つのモードがあります。既定、オプティミスティック、Full、および Custom です。 ほとんどのユーザーには、既定のモードを使用することをお勧めします。 単純な変換にはオプティミスティックモードを使用します。 すべてのメッセージを表示する場合は、フルモードを使用します。 カスタムモードでは、オプションを設定します。  
  
設定については、このドキュメントの「ユーザーインターフェイスリファレンス」セクションで説明します。 各モードでの設定と設定の適用方法の詳細については、次のトピックを参照してください。  
  
-   [プロジェクトの設定 (変換)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
-   [プロジェクトの設定 (移行)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)  
  
-   [プロジェクトの設定 (GUI)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [プロジェクトの設定 (型のマッピング)](https://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655)  
  
-   [プロジェクトの設定 (SQL Azure)](https://msdn.microsoft.com/bbb8a204-d0e4-4f0b-9709-271feb1f136e)  
  
## <a name="setting-project-options"></a>プロジェクト オプションの設定  
SSMA では、すべてのプロジェクトの既定の設定を構成できます。 これらの設定は、SSMA 構成ファイルに保存され、作成した新しいプロジェクトに適用されます。  
  
**既定のプロジェクトオプションを設定するには**  
  
1.  [**ツール**] メニューの [**既定のプロジェクト設定**] をクリックします。  
  
2.  [**既定のプロジェクト設定**] ダイアログボックスで、次のいずれかの操作を行います。  
  
    -   [移行**先のバージョン**] ドロップダウンから表示または変更する設定が必要な移行プロジェクトの種類を選択し、左側のウィンドウの下部にある [**全般**] をクリックしてから、[変換] または [**移行] または [SQL Azure**] を選択します。  
  
        > [!NOTE]  
        > SQL Azure オプションは、作成されたプロジェクトの種類が SQL Azure 場合にのみ、 **[全般**] タブで使用できます。  
  
    -   定義済みのモードを選択するには、[**モード**] ボックスの一覧で [**既定**]、[**オプティミスティック**]、または [**完全**] を選択します。  
  
    -   カスタムモードを指定するには、[**モード**] ボックスで [**カスタム**] を選択し、左ペインでオプションを選択します。次に、右ペインで設定または値をクリックし、新しい設定または値を選択または入力します。  
  
3.  
  **[OK]** をクリックして設定を保存します。  
  
また、現在のプロジェクトの設定をカスタマイズすることもできます。 これらの設定は、現在のプロジェクトファイルに保存されます。  
  
**現在のプロジェクトの設定をカスタマイズするには**  
  
1.  [**ツール**] メニューの [**プロジェクトの設定**] をクリックします。  
  
2.  [**プロジェクトの設定**] ダイアログボックスで、次のいずれかの操作を行います。  
  
    -   定義済みのモードを選択するには、[**モード**] ボックスの一覧で [**既定**]、[**オプティミスティック**]、または [**完全**] を選択します。  
  
    -   カスタムモードを指定するには、[**モード**] ボックスで [**カスタム**] を選択し、左ペインでオプションを選択します。次に、右ペインで設定または値をクリックし、新しい設定または値を選択または入力します。  
  
3.  
  **[OK]** をクリックして設定を保存します。  
  
## <a name="next-steps"></a>次の手順  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「[ソースとターゲットのデータ型のマッピング](mapping-source-and-target-data-types-accesstosql.md)」を参照してください。  
  
-   ソースデータベースとターゲットデータベースのマッピングをカスタマイズするには、「[ソースデータベースとターゲットデータベースのマッピング](mapping-source-and-target-databases-accesstosql.md)」を参照してください。  
  
-   それ以外の場合は、Access データベースオブジェクト定義を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure オブジェクト定義に変換できます。 詳細については、「 [Access データベースオブジェクトの変換](converting-access-database-objects-accesstosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
