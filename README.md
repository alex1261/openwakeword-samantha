# openwakeword-samantha

Trained using standard Colab script (modified slightly to run locally on GPU).

Configuration in training:

number_of_examples = 50000 # @param {type:"slider", min:100, max:50000, step:50}
number_of_training_steps = 30000  # @param {type:"slider", min:0, max:50000, step:100}
false_activation_penalty = 1500  # @param {type:"slider", min:100, max:5000, step:50}
config["target_phrase"] = [target_word]
config["model_name"] = config["target_phrase"][0].replace(" ", "_")
config["n_samples"] = number_of_examples
config["n_samples_val"] = max(500, number_of_examples//10)
config["steps"] = number_of_training_steps
config["target_accuracy"] = 0.5
config["target_recall"] = 0.25
config["output_dir"] = "./my_custom_model"
config["max_negative_weight"] = false_activation_penalty

config["background_paths"] = ['./audioset_16k', './fma']  # multiple background datasets are supported
config["false_positive_validation_data_path"] = "validation_set_features.npy"
config["feature_data_files"] = {"ACAV100M_sample": "openwakeword_features_ACAV100M_2000_hrs_16bit.npy"}
