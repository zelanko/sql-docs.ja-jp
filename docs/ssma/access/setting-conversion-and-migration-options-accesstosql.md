---
title: "変換と移行オプション (AccessToSQL) の設定 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6bf268665688aab98b56e0314302f8b35571e15
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="setting-conversion-and-migration-options-accesstosql"></a>変換と移行オプション (AccessToSQL) の設定
SSMA プロジェクトごとに、プロジェクト レベルのオプションを設定できます。 これらのオプションは、オブジェクトの変換方法、データの移行方法、および対象のデータ型へのソースのデータ型のマップ方法を指定します。 オブジェクトを変換する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure にデータを移行または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、設定オプションが、プロジェクトの適切なであることを確認します。  
  
## <a name="configuration-options-and-modes"></a>構成オプションとモード  
SSMA は、4 セットの構成設定とこれらの設定を構成するための 4 つのモード: 既定、Optimistic、Full、およびカスタムです。 ほとんどのユーザーには、既定のモードを使用することをお勧めします。 単純な変換では、オプティミスティック モードを使用します。 すべてのメッセージを表示する場合は、フル モードを使用します。 カスタム モードでは、オプションを設定します。  
  
設定は、このドキュメントの「ユーザー インターフェイス リファレンス」セクションで説明します。 設定と各モードの設定を適用する方法の詳細については、次のトピックを参照してください。  
  
-   [プロジェクトの設定 (変換)](http://msdn.microsoft.com/en-us/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
-   [プロジェクトの設定 (移行)](http://msdn.microsoft.com/en-us/4caebc9c-8680-4b99-a8fa-89c43161c95d)  
  
-   [プロジェクトの設定 (GUI)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [プロジェクトの設定 (型のマッピング)](http://msdn.microsoft.com/en-us/b87b9683-abed-4677-8c50-18bdba704655)  
  
-   [プロジェクトの設定 (SQL Azure)](http://msdn.microsoft.com/en-us/bbb8a204-d0e4-4f0b-9709-271feb1f136e)  
  
## <a name="setting-project-options"></a>プロジェクト オプションの設定  
SSMA では、すべてのプロジェクトの既定の設定を構成できます。 これらの設定は SSMA 構成ファイルに保存して、作成した新しいプロジェクトに適用します。  
  
**既定のプロジェクトのオプションを設定するには**  
  
1.  **ツール**メニューの **プロジェクト設定の既定の**します。  
  
2.  **プロジェクト設定の既定の** ダイアログ ボックスで、次のいずれかの操作を行います。  
  
    -   対象の設定が表示する/から変更を必要な移行プロジェクトの種類を選択**移行のターゲット バージョン**ドロップダウンで、をクリックして**全般**クリックし、左側のウィンドウの下部にある**変換または移行または SQL Azure**です。  
  
        > [!NOTE]  
        > SQL Azure のオプションが使用できる、**全般** タブの作成、プロジェクトの種類が SQL Azure である場合にのみです。  
  
    -   定義済みのモードを選択する**既定**、 **Optimistic**、または**完全**で、**モード** ボックスの一覧です。  
  
    -   カスタム モードを指定するには、次のように選択します。**カスタム**で、**モード**ボックス、左ペインでオプションを選択、設定または右側のウィンドウで値をクリックし、選択するか、新しい設定または値を入力してください。  
  
3.  をクリックして**OK**設定を保存します。  
  
現在のプロジェクトの設定をカスタマイズすることもできます。 これらの設定は、現在のプロジェクト ファイルに保存されます。  
  
**現在のプロジェクトの設定をカスタマイズするには**  
  
1.  **ツール**メニューの **プロジェクト設定**です。  
  
2.  **プロジェクト設定** ダイアログ ボックスで、次のいずれかの操作を行います。  
  
    -   定義済みのモードを選択する**既定**、 **Optimistic**、または**完全**で、**モード** ボックスの一覧です。  
  
    -   カスタム モードを指定するには、次のように選択します。**カスタム**で、**モード**ボックス、左ペインでオプションを選択、設定または右側のウィンドウで値をクリックし、選択するか、新しい設定または値を入力してください。  
  
3.  をクリックして**OK**設定を保存します。  
  
## <a name="next-steps"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください[マッピング ソースとターゲットのデータ型。](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9)  
  
-   ソースとターゲット データベースへのマッピングをカスタマイズするを参照してください[マッピング ソースとターゲット データベース。](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
-   それ以外の場合に Access データベース オブジェクトの定義を変換できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクトの定義。 詳細については、次を参照してください[データベース オブジェクトの変換へのアクセス。](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
