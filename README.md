# pyhton_get_pet_label
project
def get_pet_labels(image_dir):
    filename_list=listdir("pet_images/")
    results_dic=dict()
    items_in_dict=len(results_dic)
    print("\nEmpty Dictionary results_dic - n items=", items_in_dict)
    for idx in range(0, len(filename_list), 1):
        if filename_list[idx][0]!=".":
            pet_labels = "" 
            
            filename_end_list=filename_list[idx] #('/')[-1]
            filename_no_dot=filename_list[idx].split('.')[0]
            word_list_pet_image = filename_list[idx].split("_")
            word_list_pet_label=" ".join(word_list_pet_image)
            for word in word_list_pet_label:
               if word.isalpha():
                   pet_labels += word.lower() +" "
            pet_labels = pet_labels.strip()
            if filename_list[idx] not in results_dic:
               results_dic[filename_list[idx]] = [pet_labels] #[pet_labels[idx]]
            else:
               print("** Warning: Key=", filename_list[idx], 
                        "already exists in results_dic with value =", 
               results_dic[filename_list[idx]])
    print("\nPrinting all key-value pairs in dictionary results_dic:")
    for key in results_dic:
        print("Filename=", key, "Pet Label=", results_dic[key])
    return results_dic
