---
title: '[フラット ファイル ソース エディター] ([接続マネージャー] ページ) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 72cf4b3ee9dbcedb7a8f917328a0bdb715ba575a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072144"
---
# <a name="flat-file-source-editor-connection-manager-page"></a>[フラット ファイル ソース エディター]\ ([接続マネージャー] ページ)
  **[フラット ファイル ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、フラット ファイル ソースが使用する接続マネージャーを選択できます。 フラット ファイル ソースは、区切り形式、固定幅形式、または区切りと固定幅が混在した形式のテキスト ファイルからデータを読み取ります。  
  
 フラット ファイル ソースは、次のいずれかの種類の接続マネージャーを使用できます。  
  
-   ソースが単一のフラット ファイルの場合は、フラット ファイル接続マネージャー。 詳しくは、「 [フラット ファイル接続マネージャー](connection-manager/file-connection-manager.md)」をご覧ください。  
  
-   ソースが複数フラット ファイルで、データ フロー タスクが For ループ コンテナーなどのループ コンテナーの内部にある場合は、複数フラット ファイル接続マネージャー。 コンテナーの各ループで、フラット ファイル ソースは、複数フラット ファイル接続マネージャーが提供する次のファイル名からデータを読み込みます。 詳細については、「 [複数フラット ファイル接続マネージャー](connection-manager/multiple-flat-files-connection-manager.md)」を参照してください。  
  
 フラット ファイル ソースの詳細については、「 [Flat File Source](data-flow/flat-file-source.md)」を参照してください。  
  
## <a name="options"></a>および  
 **Flat file connection manager**  
 既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。  
  
 **[新規作成]**  
 新しい接続マネージャーを作成するには、 **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスを使用します。  
  
 **[データ ソースの NULL 値をデータ フローで NULL 値として保持する]**  
 データが抽出されたときに NULL 値を保持するかどうかを指定します。 このプロパティの既定値は **false**です。 この値が `alse` である場合、フラット ファイル変換元は変換元データの NULL 値を各列の適切な既定値で置き換えます。たとえば、文字列型の列の場合は空の文字列、数値型の列の場合は 0 です。  
  
 **プレビュー**  
 **[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 プレビューでは、最大で 200 行を表示できます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[フラット ファイル ソース エディター&#40;列] ページ&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md)   
 [[フラット ファイル ソース エディター&#40;エラー出力] ページ&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [フラット ファイル接続マネージャー](connection-manager/file-connection-manager.md)  
  
  