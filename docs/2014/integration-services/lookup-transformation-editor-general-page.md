---
title: 参照変換エディター ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.general.f1
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
caps.latest.revision: 17
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ced1e5551753ba61f81789eb8dee7d4e77dd6883
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314072"
---
# <a name="lookup-transformation-editor-general-page"></a>[参照変換エディター] ([全般] ページ)
  [参照変換エディター] ダイアログ ボックスの **[全般]** ページを使用して、キャッシュ モードや接続の種類を選択し、一致するエントリがない行の処理方法を指定します。  
  
 参照変換の詳細については、「 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[フル キャッシュ]**  
 参照変換を実行する前に、参照データセットを生成してキャッシュに読み込みます。  
  
 **[部分キャッシュ]**  
 参照変換の実行中に、参照データセットを生成します。 参照データセットに一致するエントリがある行、およびデータセットに一致するエントリがない行をキャッシュに読み込みます。  
  
 **[キャッシュなし]**  
 参照変換の実行中に、参照データセットを生成します。 キャッシュにデータは読み込まれません。  
  
 **キャッシュ接続マネージャー**  
 キャッシュ接続マネージャーを使用するように参照変換を構成します。 このオプションを選択できるのは、[フル キャッシュ] オプションを選択した場合だけです。  
  
 **[キャッシュなし]**  
 OLE DB 接続マネージャーを使用するように参照変換を構成します。  
  
 **[エントリが一致しない行の処理方法を指定する]**  
 参照データセット内で少なくとも 1 つのエントリが一致しない行を処理するためのオプションを選択します。  
  
 **[一致なしの出力に行をリダイレクトする]** を選択した場合は、行が一致なしの出力にリダイレクトされ、エラーとして処理されなくなります。 **[参照変換エディター]** ダイアログ ボックスの **[エラー出力]** ページの **[エラー]** オプションは使用できません。  
  
 **[エントリが一致しない行の処理方法を指定する]** ボックスの一覧で他のオプションを選択した場合は、行がエラーとして処理されます。 **[エラー出力]** ページの **[エラー]** オプションを使用できます。  
  
## <a name="external-resources"></a>外部リソース  
 blogs.msdn.com のブログ「 [キャッシュ モードの参照](http://go.microsoft.com/fwlink/?LinkId=219518) 」  
  
## <a name="see-also"></a>参照  
 [キャッシュ接続マネージャー](connection-manager/cache-connection-manager.md)   
 [参照変換エディター&#40;接続 ページ&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [[参照変換エディター] &#40;[列] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [参照変換エディター &#40;[詳細] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [参照変換エディター&#40;エラー出力 ページ&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)  
  
  
