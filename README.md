<img src="assets/logo.png" width="112" height="112" alt="Blyx penguin gathering the final blocks at the end of a rolled byte strip.">

# SuffixRange

Resolve an HTTP suffix-byte specification without negative offsets. This Blyx library is part of the graphql, rpc and http collection.

An inclusive last byte becomes a read length with a plus one. Handle suffixes, empty resources and unsatisfied offsets explicitly. [IETF RFC 9110, byte ranges](https://www.rfc-editor.org/rfc/rfc9110.html#section-14.1.2)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-suffixrange.git
cd blyx-suffixrange
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-suffixrange) · [Package page](https://www.blyx-lang.space/packages/suffixrange) · [Handbook](https://doc.blyx-lang.space/guide/kinglet)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-suffixrange.git vendor/suffixrange
```

```blyx
use vendor::suffixrange::suffixrange;

fn main() {
    let size = 10.0;
    let suffix = 3.0;
    let result = suffixrange_resolve(size, suffix);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
1
7
3
```

## API

`suffixrange_resolve(size, suffix)`

Returns [satisfiable, offset, length]. A suffix longer than the entity selects the full entity. Zero bytes or an empty entity produce an unsatisfied range. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| size | A nonnegative exact integer |
| suffix | A nonnegative exact integer |

## In use

[Kinglet](https://github.com/Rahulchaube1/blyx-kinglet) uses this module to plan a full or single-range HTTP response against a known representation size.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-suffixrange/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). Read the [artwork notice](assets/NOTICE.txt) for credits.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
