---
title: '[別名] プロパティ ([別名] タブ)'
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2d1498e2-129c-4ce7-88e5-408e4037243c
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 53bb19934209ee501c76317e102e5b1fcae28c4d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75306607"
---
# <a name="ltaliasgt-properties-alias-tab"></a>&lt;[別名]&gt; プロパティ ([別名] タブ)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

別名は、接続のために使用できる代替名です。 別名は、接続文字列の必須要素をカプセル化したものであり、ユーザーが選択した名前でそれらの要素を公開できます。 **[\<** Alias **> のプロパティ]** ダイアログ ボックスの **[別名]** ページでは、別名の接続文字列について各要素の表示や指定を行います。

## <a name="options"></a>オプション

**[別名]**

この接続を参照するために使用する名前 (別名) です。  

**[パイプ名]**  /  **[ポート番号]**  

接続文字列の追加要素です。 このボックスの名前は、選択したプロトコルによって異なります。 例については、最後に示すトピックを参照してください。  

**プロトコル**

接続に使用するプロトコルです。

**[サーバー]**

接続先の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前です。  

## <a name="see-also"></a>参照

- [共有メモリ プロトコルを使用した有効な接続文字列の作成](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)
- [TCP/IP を使用した有効な接続文字列の作成](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)
- [名前付きパイプを使用した有効な接続文字列の作成](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)