# srml-bdevux-assets

Substrate Runtime Module Library(SRML)

複数の資産資産を作成するためのライブラリ


<substrate-node>/runtime/Cargo.toml に下記を追加

```toml:<substrate-node>/runtime/Cargo.toml
[dependencies.bassets]
default-features = false
git = "https://github.com/ibchain/srml-bdevux-assets.git"
package = "bdevux-assets"
rev = "46d306523b91b138a147d43f80f8781d1f871fc4"
```

<substrate-node>/runtime/src/lib.rc

```rust:<substrate-node>/runtime/src/lib.rc
.
.
.
impl bassets::Trait for Runtime {
  type Event = Event;
}
.
.
.
construct_runtime!(
  pub enum Runtime with Log(InternalLog: DigestItem<Hash, AuthorityId, AuthoritySignature>) where
    Block = Block,
    NodeBlock = opaque::Block,
    UncheckedExtrinsic = UncheckedExtrinsic
  {
  .
  .
  .
    Bdevux: bassets::{Module, Call, Storage, Event<T>},
  }
);
.
.
.
```

