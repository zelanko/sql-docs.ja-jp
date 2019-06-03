---
title: Azure Data Lake Store Destination | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSDEST.F1
- sql14.dts.designer.afpadlsdest.f1
ms.assetid: 4c4f504f-dd2b-42c5-8a20-1a8ad9a5d632
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d934cafef262f5c07b5eeac95d65abd776d8bb35
ms.sourcegitcommit: fc0eb955b41c9c508a1fe550eb5421c05fbf11b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66403034"
---
# <a name="azure-data-lake-store-destination"></a>Azure Data Lake Store Destination

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  **Azure Data Lake Store Destination** コンポーネントは、SSIS パッケージが Azure Data Lake Store にデータを書き込めるようにします。 サポートされるファイル形式は、テキスト、Avro、ORC です。 
  
 **Azure Data Lake Store Destination** は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。
 
> [!NOTE]
> Azure Data Lake Store 接続マネージャーとこれを使用するコンポーネント (つまり、Azure Data Lake Store Source と Azure Data Lake Store Destination) がサービスに接続できるようにするために、必ず最新バージョンの Azure Feature Pack を [こちら](https://www.microsoft.com/download/details.aspx?id=49492)からダウンロードしてください。 

## <a name="configure-the-azure-data-lake-store-destination"></a>Azure Data Lake Store Destination を構成する  
1. **Azure Data Lake Store Destination** をデータ フロー デザイナーにドラッグ アンド ドロップし、ダブルクリックしてエディターを表示します。  

2.  **[Azure Data Lake Store connection manager (Azure Data Lake Store 接続マネージャー)]** フィールドに、既存の Azure Data Lake Store 接続マネージャーを指定するか、Azure Data Lake Store サービスを参照する新しいものを作成します。  
  
    1.  **[ファイル パス]** フィールドには、データを書き込むファイルの名前を指定します。 このファイルが既に存在する場合、その内容は上書きされます。  
  
    2.  **[ファイル形式]** フィールドには、使用するファイル形式を指定します。  
  
       テキスト ファイル形式の場合は、 **[列の区切り文字]** に値を指定する必要があります。 さらに、ファイルの 1 行目に列名が含まれている場合は、 **[先頭データ行を列名として使用する]** も指定する必要があります。  

       ファイル形式が ORC の場合は、適切なプラットフォームの Java Runtime Environment (JRE) をインストールする必要があります。
  
3.  接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。  

## <a name="prerequisite-for-orc-file-format"></a>ORC ファイル形式の前提条件
ORC ファイル形式を使用するには Java が必須です。
Java ビルドのアーキテクチャ (32/64 ビット) は、SSIS ランタイムのそれと一致しなければ使用できません。
次の Java ビルドがテストされています。

- [Zulu の OpenJDK 8u192](https://www.azul.com/downloads/zulu/zulu-windows/)
- [Oracle の Java SE Runtime Environment 8u192](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)

### <a name="set-up-zulus-openjdk"></a>Zulu の OpenJDK を設定する
1. インストール zip パッケージをダウンロードし、抽出します。
2. コマンド プロンプトから `sysdm.cpl` を実行します。
3. **[詳細設定]** タブの **[環境変数]** を選択します。
4. **[システム変数]** セクションで **[新規]** を選択します。
5. **[変数名]** に「`JAVA_HOME`」と入力します。
6. **[ディレクトリの参照]** を選択し、解凍したフォルダーに移動し、`jre` サブフォルダーを選択します。
   **[OK]** を選択すると、**変数の値**が自動的に入力されます。
7. **[OK]** を選択し、 **[新しいシステム変数]** ダイアログ ボックスを閉じます。
8. **[OK]** を選択し、 **[環境変数]** ダイアログ ボックスを閉じます。
9. **[OK]** を選択して **[システム プロパティ]** ダイアログ ボックスを閉じます。

### <a name="set-up-oracles-java-se-runtime-environment"></a>Oracle の Java SE Runtime Environment を設定する
1. exe インストーラーをダウンロードし、実行します。
2. インストーラーの指示に従い、設定を完了します。