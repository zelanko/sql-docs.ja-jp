---
description: セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列のクエリを実行する
title: セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列のクエリを実行する | Microsoft Docs
ms.custom: ''
ms.date: 10/31/2019
ms.reviewer: vanto
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15'
ms.openlocfilehash: 517e2a0beb7364507d585d9cd729069048cf1c82
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477563"
---
# <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列のクエリを実行する
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

このチュートリアルでは、[セキュリティで保護されたエンクレーブが設定された Always Encrypted](always-encrypted-enclaves.md) に対してサーバー側のセキュリティで保護されたエンクレーブを使用して、暗号化された列に対するクエリを実行する場合の、一般的な考慮事項について説明します。 

次の種類のクエリには、セキュリティで保護されたエンクレーブの使用が含まれます。
- エンクレーブ対応キーを使用するインプレース暗号化操作をトリガーするクエリ。「[Transact-SQL を使用してインプレースでの列の暗号化を構成する](always-encrypted-enclaves-configure-encryption-tsql.md)」をご覧ください。
- *高度なクエリ* - ランダム化された暗号化およびエンクレーブ対応キーを使用して暗号化された列に対する範囲比較またはパターン マッチング操作。
- ランダム化された暗号化およびエンクレーブ対応キーを使用して、暗号化された列のインデックスを作成または更新するクエリ。 詳細については、「[セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列でインデックスを作成して使用する](always-encrypted-enclaves-create-use-indexes.md)」を参照してください。

> [!NOTE]
> 高度なクエリとインデックスは、ランダム化された暗号化を使用するエンクレーブ対応列 (エンクレーブ対応列の暗号化キーで暗号化された列) でのみサポートされています。 決定論的暗号化では、高度なクエリやインデックスはサポートされていません。

> [!NOTE]
> 暗号化された文字列型の列で高度なクエリを使用するには、バイナリ 2 並べ替え順序 (BIN2 照合順序) による照合順序が列で使用されている必要があります。 


## <a name="next-steps"></a>次の手順
- [セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列のクエリを SSMS で実行する](always-encrypted-enclaves-query-columns-ssms.md)

## <a name="see-also"></a>参照
- [チュートリアル:SSMS を使用したセキュリティで保護されたエンクレーブを持つ Always Encrypted の概要](../tutorial-getting-started-with-always-encrypted-enclaves.md)

