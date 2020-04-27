---
title: 参照変換のアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: eae7433569972c217161f1681b2f7089c7604335
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66091507"
---
# <a name="upgrade-lookup-transformations"></a>参照変換のアップグレード
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] を [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードする場合、パッケージに変更を加え、参照変換でこれらの新しい機能を利用することを検討してください。 この変換では、[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] で使用可能なキャッシュの種類とデータ出力オプションがサポートされます。 キャッシュとデータ出力の詳細については、「[参照変換](../../integration-services/data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] で使用可能なキャッシュの種類は、完全キャッシュ、部分キャッシュ、およびキャッシュなしです。 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] では、これらのいずれかの種類のキャッシュを使用するように参照変換を構成できます。 部分キャッシュまたはキャッシュなしの実装方法の詳細については、「[キャッシュなしモードまたは部分キャッシュモードでの参照の実装](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md)」を参照してください。 完全キャッシュを実装する方法については、「[キャッシュ接続マネージャーを使用してフルキャッシュモードの参照変換を実装](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)する」および「 [OLE DB 接続マネージャーを使用してフルキャッシュモードの参照変換を実装](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)する」を参照してください。  
  
 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] では、参照変換は 1 つの入力、1 つの出力、および 1 つのエラー出力になっていました。 参照データセットに一致するエントリがある入力の行は、出力で処理されていました。 一致するエントリがない入力の行はエラーとして処理され、エラー出力にリダイレクトされていました。 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] では、参照変換の出力は 2 つ (一致する出力と一致しない出力) になります。  
  
 既定では、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で作成された参照変換を実行すると、[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] では一致するエントリのない行はエラーとして処理され、その行はエラー出力にリダイレクトできます。 行をエラーではないものとして処理し、それらの行を、一致しない出力にリダイレクトするように参照変換を構成することもできます。  
  
 詳細については、「 [[参照変換エディター] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [参照変換](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
