---
title: "キャッシュ接続マネージャー エディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.cacheconnection.f1
ms.assetid: 0d8f9324-0c35-4eea-b06d-da3cc2426d2c
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2c8fd51cc4abae8c4756a896809b75d6c449862d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="cache-connection-manager-editor"></a>[キャッシュ接続マネージャー エディター]
  キャッシュ接続マネージャーでは、キャッシュ変換またはキャッシュ ファイル (.caw) から参照データセットを読み取り、そのデータをキャッシュ ファイルに保存できます。 データは常にメモリに格納されます。  
  
> [!NOTE]  
>  キャッシュ接続マネージャーでは、バイナリ ラージ オブジェクト (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE はサポートされません。 参照データセットに BLOB データ型が含まれている場合、パッケージを実行するとコンポーネントは失敗します。 **[キャッシュ接続マネージャー エディター]** を使用して、列のデータ型を変更できます。  
  
 参照変換は、参照データセットで参照を実行します。  
  
 **[キャッシュ接続マネージャー エディター]** ダイアログ ボックスには、次のタブがあります。  
  
-   [[全般] タブ](../../integration-services/connection-manager/cache-connection-manager-editor.md#generaltab)  
  
-   [[列] タブ](../../integration-services/connection-manager/cache-connection-manager-editor.md#columnstab)  
  
 キャッシュ接続マネージャーの詳細については、「 [Cache Connection Manager](../../integration-services/connection-manager/cache-connection-manager.md)」を参照してください。  
  
##  <a name="generaltab"></a> [全般] タブ  
 **[キャッシュ接続マネージャー エディター]** ダイアログ ボックスの **[全般]** タブを使用すると、ファイルからキャッシュを読み取るか、キャッシュをファイルに保存するかを指定できます。  
  
### <a name="options"></a>オプション  
 **[接続マネージャー名]**  
 ワークフローにおけるキャッシュ接続マネージャーの一意な名前を指定します。 指定された名前は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーに表示されます。  
  
 **Description**  
 接続の説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的に従って記述することをお勧めします。  
  
 **[ファイル キャッシュを使用する]**  
 キャッシュ ファイルを使用するかどうかを示します。  
  
> [!NOTE]  
>  パッケージの保護レベルは、キャッシュ ファイルに適用されません。 キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。 特定のアカウントに対してのみアクセスを有効にする必要があります。 詳細については、「 [パッケージで使用されるファイルへのアクセス](../../integration-services/security/security-overview-integration-services.md#files)」を参照してください。  
  
 キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成すると、接続マネージャーは、次のいずれかの処理を実行します。  
  
-   データ フロー内のデータ ソースからキャッシュ接続マネージャーにデータが書き込まれるようにキャッシュ変換が構成されている場合は、データをファイルに保存します。 詳しくは、「 [Cache Transform](../../integration-services/data-flow/transformations/cache-transform.md)」をご覧ください。  
  
-   キャッシュ ファイルからデータを読み取ります。  
  
 **ファイル名**  
 キャッシュ ファイルのパスと名前を入力します。  
  
 **参照**  
 キャッシュ ファイルを指定します。  
  
 **[メタデータの更新]**  
 キャッシュ接続マネージャーで列のメタデータを削除し、選択したキャッシュ ファイルの列のメタデータでキャッシュ接続マネージャーを再設定します。  
  
##  <a name="columnstab"></a> [列] タブ  
 **[キャッシュ接続マネージャー エディター]** ダイアログ ボックスの **[列]** タブを使用すると、キャッシュ内の各列のプロパティを構成できます。  
  
### <a name="options"></a>オプション  
 **列**  
 列名を指定します。  
  
 **[インデックス位置]**  
 各列のインデックス位置を指定して、インデックス列として使用する列を指定します。 インデックスは 1 つまたは複数の列のコレクションです。  
  
 インデックス以外の列の場合、インデックス位置は 0 です。  
  
 インデックス列の場合、インデックスの位置は連続した正の数になります。 この数は、参照変換が参照データセットの行と入力データ ソースの行を比較する順序を示します。 最も固有な値を含む列に、最も小さいインデックス位置を指定する必要があります。  
  
> [!NOTE]  
>  参照変換がキャッシュ接続マネージャーを使用するように構成されている場合、参照データセット内のインデックス列のみ入力列にマップできます。 また、すべてのインデックス列をマップする必要があります。  
  
 **型**  
 列のデータ型を指定します。  
  
 **長さ**  
 列のデータ型を指定します。 **[長さ]**は、そのデータ型で使用できる範囲内であれば更新できます。  
  
 **有効桁数**  
 特定の列のデータ型の有効桁数を指定します。 有効桁数は、数値全体の桁数です。 **[有効桁数]**は、そのデータ型で使用できる範囲内であれば更新できます。  
  
 **Scale**  
 特定の列のデータ型の小数点以下桁数を指定します。 小数点以下桁数は、数値の中で小数点より右側の桁数です。 **[小数点以下桁数]**は、そのデータ型で使用できる範囲内であれば更新できます。  
  
 **コード ページ**  
 列の型のコード ページを指定します。 **[コード ページ]**は、そのデータ型で使用できる範囲内であれば更新できます。  
  
## <a name="see-also"></a>参照  
 [参照変換](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
