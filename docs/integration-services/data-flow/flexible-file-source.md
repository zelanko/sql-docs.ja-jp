---
title: 柔軟なファイル ソース | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpextfilesrc.f1
- sql14.dts.designer.afpextfilesrc.f1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3e396e40f30571969b347c464687321b3b038212
ms.sourcegitcommit: fa2afe8e6aec51e295f55f8cc6ad3e7c6b52e042
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462536"
---
# <a name="flexible-file-source"></a>柔軟なファイル ソース

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

**柔軟なファイル ソース** コンポーネントにより、SSIS パッケージがサポートされているさまざまなストレージ サービスからデータを読み取れるようになります。
現在サポートされているストレージ サービスは次のとおりです。

- [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)
  
柔軟なファイル ソースのエディターを表示するには、データ フロー デザイナー上に**柔軟なファイル ソース**をドラッグ アンド ドロップし、これをダブルクリックしてエディターを開きます。
  
**柔軟なファイル ソース**は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。  
  
次のプロパティは、**柔軟なファイル ソース エディター**で利用できます。

- **[File Connection Manager Type]\(ファイル接続マネージャーの種類\):** ソース接続マネージャーの種類を指定します。 そして、指定された種類の既存のものを選択するか、新しいものを作成します。
- **[フォルダー パス]:** ソース フォルダーのパスを指定します。
- **ファイル名:** ソース ファイル名を指定します。
- **[ファイル形式]:** ソース ファイル形式を指定します。 サポートされている形式は、**テキスト**、**Avro**、**ORC**、**Parquet** です。
- **[列区切り文字]:** 列区切り記号として使用される文字を指定します (複数文字の区切り記号はサポートされていません)。
- **[First row as the column name]\(先頭行を列名にする\):** 先頭行を列名として扱うかどうかを指定します。
- **[Decompress the file]\(ファイル圧縮の解除\):** ソース ファイルの圧縮を解除するかどうかを指定します。
- **[圧縮の種類]:** ソース ファイルの圧縮形式を指定します。 サポートされている形式は **GZIP**、**DEFLATE**、**BZIP2** です。
  
次のプロパティは、**詳細エディター**で利用できます。

- **rowDelimiter:** ファイルの行を区切るための文字。 許可される文字は 1 つだけです。 **既定**値は \r\n です。
- **escapeChar:** 入力ファイルの列区切り記号をエスケープするための特殊文字。 escapeChar と quoteChar の両方をテーブルに指定することはできません。 許可される文字は 1 つだけです。 既定値はありません。
- **quoteChar:** 文字列値を引用符で囲むための文字。 引用符文字内の列区切り記号と行区切り記号は文字列値の一部として扱われます。 このプロパティは、入力と出力の両方のデータセットに適用できます。 escapeChar と quoteChar の両方をテーブルに指定することはできません。 許可される文字は 1 つだけです。 既定値はありません。
- **nullValue:** null 値を表すための 1 つまたは複数の文字。 **既定**値は \N です。
- **encodingName:** エンコーディング名を指定します。 [Encoding.EncodingName](https://docs.microsoft.com/en-us/dotnet/api/system.text.encoding?redirectedfrom=MSDN&view=netframework-4.8) プロパティを参照してください。
- **skipLineCount:** 入力ファイルからデータを読むとき、スキップする空ではない行の数を示します。 skipLineCount と firstRowAsHeader の両方が指定されている場合、行が最初にスキップされ、次に、入力ファイルからヘッダー情報が読まれます。
- **treatEmptyAsNull:** 入力ファイルからデータを読むとき、null 値として null または空の文字列を扱うことを指定します。 **既定**値は True です。

接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。

**ORC/Parquet ファイル形式の前提条件**

ORC/Parquet ファイル形式を使用するには Java が必須です。
Java ビルドのアーキテクチャ (32/64 ビット) は、SSIS ランタイムのそれと一致しなければ使用できません。
次の Java ビルドがテストされています。

- [Zulu の OpenJDK 8u192](https://www.azul.com/downloads/zulu/zulu-windows/)
- [Oracle の Java SE Runtime Environment 8u192](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)

**Zulu の OpenJDK を設定する**

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

**Oracle の Java SE Runtime Environment を設定する**

1. exe インストーラーをダウンロードし、実行します。
2. インストーラーの指示に従い、設定を完了します。
