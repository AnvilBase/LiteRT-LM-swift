# LiteRT-LM Swift, with an activation-type setting

The Swift package from [google-ai-edge/LiteRT-LM](https://github.com/google-ai-edge/LiteRT-LM) at v0.17.0 — `Package.swift` and `swift/` only, pointing at Google's own prebuilt `CLiteRTLM` xcframeworks — plus one addition: `EngineConfig(activationDataType:)`, which calls `litert_lm_engine_settings_set_activation_data_type`.

Anvil needs it because the prebuilt Metal accelerator's FLOAT16 path scrambles digits for Gemma 4 on iOS (upstream issue [#2814](https://github.com/google-ai-edge/LiteRT-LM/issues/2814)); FLOAT32 activations on the GPU is the documented workaround, and the upstream Swift wrapper has no way to set it. Drop this fork the day upstream exposes the setting or fixes the fp16 kernels.
