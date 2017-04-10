---
title: "[参照変換エディター] ([全般] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.lookuptransformation.general.f1"
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# [参照変換エディター] ([全般] ページ)
  [参照変換エディター] ダイアログ ボックスの **[全般]** ページを使用して、キャッシュ モードや接続の種類を選択し、一致するエントリがない行の処理方法を指定します。  
  
 参照変換の詳細については、「 [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
## オプション  
 **[フル キャッシュ]**  
 参照変換を実行する前に、参照データセットを生成してキャッシュに読み込みます。  
  
 **[部分キャッシュ]**  
 参照変換の実行中に、参照データセットを生成します。 参照データセットに一致するエントリがある行、およびデータセットに一致するエントリがない行をキャッシュに読み込みます。  
  
 **[キャッシュなし]**  
 参照変換の実行中に、参照データセットを生成します。 キャッシュにデータは読み込まれません。  
  
 **キャッシュ接続マネージャー**  
 キャッシュ接続マネージャーを使用するように参照変換を構成します。 このオプションを選択できるのは、[フル キャッシュ] オプションを選択した場合だけです。  
  
 **OLE DB 接続マネージャー**  
 OLE DB 接続マネージャーを使用するように参照変換を構成します。  
  
 **[エントリが一致しない行の処理方法を指定する]**  
 参照データセット内で少なくとも 1 つのエントリが一致しない行を処理するためのオプションを選択します。  
  
 **[一致なしの出力に行をリダイレクトする]**を選択した場合は、行が一致なしの出力にリダイレクトされ、エラーとして処理されなくなります。 **[参照変換エディター]** ダイアログ ボックスの **[エラー出力]** ページの **[エラー]** オプションは使用できません。  
  
 **[エントリが一致しない行の処理方法を指定する]** ボックスの一覧で他のオプションを選択した場合は、行がエラーとして処理されます。 **[エラー出力]** ページの **[エラー]** オプションを使用できます。  
  
## 外部リソース  
 blogs.msdn.com のブログ「 [キャッシュ モードの参照](http://go.microsoft.com/fwlink/?LinkId=219518) 」  
  
## 参照  
 [キャッシュ接続マネージャー](../../../integration-services/data-flow/transformations/cache-connection-manager.md)   
 [参照変換エディター ([接続] ページ)](../Topic/Lookup%20Transformation%20Editor%20\(Connection%20Page\).md)   
 [参照変換エディター ([列] ページ)](../Topic/Lookup%20Transformation%20Editor%20\(Columns%20Page\).md)   
 [参照変換エディター ([詳細設定] ページ)](../Topic/Lookup%20Transformation%20Editor%20\(Advanced%20Page\).md)   
 [参照変換エディター ([エラー出力] ページ)](../Topic/Lookup%20Transformation%20Editor%20\(Error%20Output%20Page\).md)  
  
  