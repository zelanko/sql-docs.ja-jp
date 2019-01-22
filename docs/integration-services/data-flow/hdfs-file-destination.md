---
title: HDFS ファイル変換先 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f18f6b0516ab9ae417251e49f5a3cf24fd2aa997
ms.sourcegitcommit: 1c01af5b02fe185fd60718cc289829426dc86eaa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185008"
---
# <a name="hdfs-file-destination"></a>HDFS ファイル変換先
  HDFS ファイル変換先コンポーネントは、SSIS パッケージが HDFS ファイルにデータを書き込めるようにします。 サポートされるファイル形式は、テキスト、Avro、および ORC です。  
  
 HDFS ファイル変換先を構成するには、HDFS ファイル ソースをデータ フロー デザイナー上にドラッグ アンド ドロップし、このコンポーネントをダブルクリックしてエディターを開きます。  
  
 ![HDFS ファイル変換先エディター](../../integration-services/data-flow/media/hdfs-file-dest.png "HDFS ファイル変換先エディター")  
  
## <a name="options"></a>オプション  
 **[Hadoop File Destination Editor]** (Hadoop ファイル変換先エディター) ダイアログ ボックスの **[全般]** タブで、次のオプションを構成します。  
  
|フィールド|[説明]|  
|-----------|-----------------|  
|**Hadoop 接続**|既存の Hadoop 接続マネージャーを指定するか、新しい Hadoop 接続マネージャーを作成します。 この接続マネージャーは、HDFS ファイルがホストされる場所を示します。|  
|**ファイル パス**|HDFS ファイルの名前を指定します。|  
|**ファイル形式**|HDFS ファイルの形式を指定します。 テキスト、Avro、または ORC 形式を選択できます。|  
|**Column delimiter character (列区切り文字)**|テキスト形式を選択した場合は、列区切り文字を指定します。|  
|**先頭データ行を列名として使用する**|テキスト形式を選択した場合は、ファイルの最初の行に列の名前が含まれるかどうかを示します。|  
  
 これらのオプションを構成した後、 **[列]** タブを選択し、データ フローのソース列を変換先列にマップします。  

::: moniker range=">= sql-server-ver15"
## <a name="prerequisite-for-orc-format"></a>ORC 形式の前提条件

ORC ファイル形式を使用するには、プラットフォームに合わせたバージョン 1.7.51 以降の Java Runtime Environment (JRE) をインストールする必要があります。

Zulu JRE と Oracle JRE の両方に対応しています。
-   [Zulu JRE](https://www.azul.com/downloads/zulu/zulu-windows/)
-   [Oracle JRE](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html)

### <a name="set-up-the-zulu-jre"></a>Zulu JRE を設定する

1. Zulu OpenJDK インストール zip パッケージをダウンロードし、抽出します。

2.  コマンド プロンプトから `sysdm.cpl` を実行します。

3. **[詳細設定]** タブの **[環境変数]** を選択します。

4. **[システム変数]** セクションで **[新規]** を選択します。

5. **[変数名]** に「`JAVA_HOME`」と入力します。

6. **[ディレクトリの参照]** を選択し、Zulu OpenJDK インストール フォルダーに移動し、`jre` サブフォルダーを選択します。 [OK] を選択します。 変数の値は自動的に入力されます。

7. **[OK]** を選択し、**[新しいシステム変数]** ダイアログ ボックスを閉じます。

8. **[OK]** を選択し、[環境変数] ダイアログ ボックスを閉じます。

### <a name="set-up-the-oracle-jre"></a>Oracle JRE を設定する

1. Oracle JRE exe インストーラーをダウンロードし、実行します。

1. インストーラーの指示に従い、設定を完了します。

::: moniker-end

## <a name="see-also"></a>参照  
 [Hadoop 接続マネージャー](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [HDFS ファイル ソース](../../integration-services/data-flow/hdfs-file-source.md)  
